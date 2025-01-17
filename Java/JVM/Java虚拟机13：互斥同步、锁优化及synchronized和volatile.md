**互斥同步**

互斥同步（Mutual Exclusion & Synchronization）是常见的一种并发正确性保证手段。同步是指子啊多个线程并发访问共享数据时，保证共享数据在同一时刻只能被一个（或者是一些，使用信号量的时候）线程使用。而互斥是实现同步的一种手段，临界区（Critial Section）、互斥量（Mutex）和信号量（Semaphore）都是主要的互斥实现方式。因此，在这四个字里面，互斥是因，同步是果；互斥是方法，同步是目的。

 

**synchronized的实现**

在Java中，大家都知道，synchronized关键字是最基本的互斥同步手段。看一段简单的代码：

```java
public static void main(String[] args)
{
    synchronized (TestMain.class)
    {
        
    }
}
```

这段代码被编译之后是这样的：

```
 1 public static void main(java.lang.String[]);
 2   flags: ACC_PUBLIC, ACC_STATIC
 3   Code:
 4     stack=2, locals=1, args_size=1
 5        0: ldc           #1                  // class com/xrq/test53/TestMain
 6        2: dup
 7        3: monitorenter
 8        4: monitorexit
 9        5: return
10     LineNumberTable:
11       line 7: 0
12       line 11: 5
13     LocalVariableTable:
14       Start  Length  Slot  Name   Signature
15              0       6     0  args   [Ljava/lang/String;
```



关键就在第7行和第8行，在源代码被编译之后，Java虚拟机会利用monitorenter和monitorexit条字节码指令来处理synchronized这个关键字。

根据虚拟机规范的要求，在执行monitorenter指令时，首先要尝试获取对象的锁，如果这个对象没有被锁定，或者当前线程已经拥有了那个对象的锁，把锁的计数器加1，相应地，在执行monitorexit指令时会将锁计数器减1，当计数器为0时，锁就会被释放。如果获取对象锁失败，那当前线程就要阻塞等待，直到对象锁被另外一个线程释放为止。

关于monitorenter和monitorexit，有两点是要特别注意的：

1、synchronized同步块对同一条线程来说是可重入的，不会出现把自己锁死的问题

2、同步块在已进入的线程执行完之前，会阻塞后面其它线程的进入

因为Java的线程是映射到操作系统的原生线程之上的，如果要阻塞或者唤醒一个线程，都需要操作系统来帮忙完成，这就需要**从用户态转换到核心态中**，因此状态转换需要耗费很多的处理器时间，对于代码简单的同步块，状态转换消耗的时间有可能比用户代码执行的时间还长，所以synchronized是Java语言中一个重量级（Heavyweight）锁，有经验的程序员都会在确实必要的情况下才使用这种操作。

顺便看一下HotSpot虚拟机对象头Mark Word：

| **存 储 内 存**                      | **标 识 位** | **状    态**       |
| ------------------------------------ | ------------ | ------------------ |
| 对象哈希吗、对象分代年龄             | 01           | 未锁定             |
| 指向锁记录的指针                     | 00           | 轻量级锁定         |
| 指向重量级锁的指针                   | 10           | 膨胀（重量级锁定） |
| 空，不需要记录信息                   | 11           | GC标记             |
| 偏向线程ID、偏向时间戳、对象分代年龄 | 01           | 可偏向             |

看到有一个重量级锁定，指的就是重量级锁。

 

**volatile的实现**

对于volatile关键字，一个被volatile关键字修饰的变量，在生成汇编语言之后，大致会多出这么一条指令：

```
0x01a3de24:lock addl $0x0,(%esp)      ;...f0830424 00
```

这个操作相当于是一个内存屏障，只有一个CPU访问内存时，并不需要内存屏障；但如果有两个或者更多CPU访问同一块内存时，且其中一个在观测另外一个，就需要内存屏障来保证一致性了。这句指令中的"addl $0x0,(%esp)"（把esp寄存器的值加0）显然是一个空操作（采用这个空操作而不是空指令nop是因为IA32手册规定lock前缀不允许配合nop指令使用），关键在于lock前缀，查询IA32手册，它的作用是使得本CPU的Cache写入了内存，该写入动作也会引起别的CPU或者别的内核无效化其Cache，这种操作相当于对Cache中的变量做了一次"store和write"操作，所以通过这样一个空操作，可让前面volatile变量的修改对其他CPU立即可见。

 

**自旋锁与自适应自旋**

互斥同步，对性能影响最大的是阻塞的实现，挂起线程和恢复线程的操作都需要转入内核状态完成，这些操作给系统的并发性能带来了很大的压力。同时，虚拟机开发团队也注意到很多应用上，共享数据的锁定状态只会持续很短的一段时间，为了这段时间去挂起和恢复线程并不值得。如果物理机上有一个以上的处理器，能让两个或两个以上的线程同时并行执行，我们就可以让后面请求锁的那个线程"稍等一下"，但不放弃处理器的执行时间，看看持有锁的线程是否很快就会释放锁。为了让线程等待，我们只需要**让线程执行一个忙循环（自旋），这项技术就是所谓的自旋锁**。

在JDK1.4.2就已经引入了自旋锁，只不过默认是关闭的。**自旋不能代替阻塞**，且先不说处理器数量的要求，自旋等待本身虽然避免了线程切换的开销，但是它是要占据处理器时间的，因此如果锁被占用的时间很短，自旋等待的效果就非常好；反之，如果锁被占用的时间很长，那么自旋的线程只会白白消耗处理器资源，而不会做任何有用的工作，反而会带来性能上的浪费。因此自选等待必须有一定的限度，如果自旋超过了限定的次数仍然没有成功获得锁，就应当使用传统的方式去挂起线程了，自旋次数的默认值是10。

在JDK1.6之后引入了自适应的自旋锁。自适应意味着自旋的时间不再固定了，而是由前一次在同一个锁上自旋的时间以及锁的拥有者的状态来决定。如果在同一个锁对象上，自旋等待刚刚获得过锁，并且持有锁的线程正在运行中，那么虚拟机就会认为这次自旋也很有可能再次成功，进而它将允许自旋等待持续相对更长的时间，比如100个循环。另外如果对于某一个锁，自旋很少成功获得过，那么在以后要获得这个锁时将可能忽略掉自旋过程，以避免浪费处理器资源。有了自适应自旋，随着程序运行和性能监控信息的不断完善，虚拟机对程序锁的状况预测就会越来越准确。

 

**锁消除**

锁消除是指虚拟机即时编译器在运行时，对一些代码上要求同步，但是被检测到不可能存在共享数据竞争的锁进行消除。锁消除的主要判定依据来源于[逃逸分析](http://www.cnblogs.com/xrq730/p/4857820.html)的支持，如果判断在一段代码中，堆上所有数据都不会逃逸出去从而被其他线程访问到，那就可以把它们当做栈上数据对待，认为它们是线程私有的，同步加锁自然无需进行。

 

**锁粗化**

原则上，我们在编写代码的时候，总是推荐将同步块的作用范围限制得尽量小----只在共享数据的实际作用域中才进行同步，这样是为了使得需要同步的操作数尽可能变小，如果存在锁竞争，那等待锁的线程也能尽快拿到锁。

大部分情况下，上面的原则都是正确的，但是如果一系列的连续操作都对同一个对象反复加锁和解锁，甚至加锁操作是出现在循环体中的，那即使没有线程竞争，频繁地进行互斥同步操作也会导致不必要的性能损耗。

如果这么说不够直观，那么想想某段代码反复使用StringBuffer的append方法拼接字符串的例子吧。