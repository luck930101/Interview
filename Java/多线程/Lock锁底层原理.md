当多个线程需要访问某个公共资源的时候，我们知道需要通过加锁来保证资源的访问不会出问题。java提供了**两种方式来加锁**，

一种是关键字：synchronized，一种是concurrent包下的lock锁。

synchronized是**java底层支持的**，而concurrent包则是**jdk实现**。

 

关于synchronized的原理可以阅读再有人问你synchronized是什么，就把这篇文章发给他。

在这里，我会用尽可能少的代码，尽可能轻松的文字，尽可能多的图来看看lock的原理。

我们以ReentrantLock为例做分析，其他原理类似。

我把这个过程比喻成一个做菜的过程，有什么菜，做法如何？

**我先列出lock实现过程中的几个关键词：计数值、双向链表、CAS+自旋**

 

我们以**ReentrantLock**为例做分析，其他原理类似。

   可以实现公平锁和非公平锁（ 当有线程竞争锁时，当前线程会首先尝试获得锁而不是在队列中进行排队等候，这对于那些已经在队列中排队的线程来说显得不公平，这也是非公平锁的由来），默认情况下为非公平锁。

**实现原理**

**ReentrantLock() 干了啥**

```java
  public ReentrantLock() {
        sync = new NonfairSync();
    }
```

在lock的构造函数中，定义了一个NonFairSync，

static final class NonfairSync extends Sync

NonfairSync 又是继承于Sync

abstract static class Sync extends AbstractQueuedSynchronizer

 

一步一步往上找，找到了

这个鬼AbstractQueuedSynchronizer（简称AQS），最后这个鬼，又是继承于AbstractOwnableSynchronizer(AOS)，AOS主要是保存获取当前锁的线程对象，代码不多不再展开。最后我们可以看到几个主要类的继承关系：

​                      ![img](https://img-blog.csdnimg.cn/20190107012324620.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

   FairSync 与 NonfairSync的区别在于，是不是保证获取锁的公平性，因为默认是NonfairSync（**非公平性**），我们以这个为例了解其背后的原理。

其他几个类代码不多，最后的主要代码都是在**AQS**中，我们先看看这个类的主体结构。

**看看AbstractQueuedSynchronizer是个什么**

![img](https://img-blog.csdnimg.cn/20190107012324750.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

再看看Node是什么？

![img](https://img-blog.csdnimg.cn/20190107012324807.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

看到这里的同学，是不是有种热泪盈眶的感觉，这尼玛，不就是**双向链表**么？我还记得第一次写这个数据结构的时候，发现居然还有这么神奇的一个东西。

最后我们可以发现锁的存储结构就两个东西:**"****双向链表****" + "****int类型状态****"。**

简单来说，ReenTrantLock的实现是一种**自旋锁**，通过循环调用CAS操作来实现加锁。它的性能比较好也是因为**避免了使线程进入内核态的阻塞状态。**想尽办法避免线程进入内核的阻塞状态是我们去分析和理解锁设计的关键钥匙。

需要注意的是，他们的变量都被"**transient**和**volatile**修饰。

![img](https://img-blog.csdnimg.cn/20190107012324812.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

 

一个int值，一个双向链表是如何烹饪处理锁这道菜的呢，Doug Lea大神就是大神，

我们接下来看看，**如何获取锁？**

 

**lock.lock()怎么获取锁？**

```java
public void lock() {
    sync.lock();
}
```

可以看到调用的是，**NonfairSync.lock()**

![img](https://img-blog.csdnimg.cn/20190107012324823.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

看到这里，我们基本有了一个大概的了解，还记得之前AQS中的**int类型的state值，**

这里就是通过**CAS**（乐观锁）去修改state的值(**锁状态值**)。lock的基本操作还是通过**乐观锁**来实现的。

**获取锁通过CAS**，那么没有获取到锁，**等待获取锁**是如何实现的？我们可以看一下else分支的逻辑，acquire方法：

```java
public final void acquire(int arg) {


    if (!tryAcquire(arg) &&

        acquireQueued(addWaiter(Node.EXCLUSIVE), arg))

        selfInterrupt();

}
```

这里干了三件事情：

- tryAcquire：会尝试再次通过CAS获取一次锁。
- addWaiter：将当前线程加入上面锁的双向链表（等待队列）中
- acquireQueued：通过自旋，判断当前队列节点是否可以获取锁。

 

**addWaiter()** **添加当前线程到等待链表中**

![img](https://img-blog.csdnimg.cn/20190107012324820.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

可以看到，通过CAS确保能够在线程安全的情况下，将当前线程加入到链表的**尾部。**

enq是个自旋+上述逻辑，有兴趣的可以翻翻源码。

 

**acquireQueued()  自旋+CAS****尝试获取锁**

![img](https://img-blog.csdnimg.cn/20190107012324870.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

可以看到，当当前**线程到头部的时候，尝试CAS更新锁状态，如果更新成功表示该等待线程获取成功。从头部移除。**

 

**每一个线程都在 自旋+CAS**

![img](https://img-blog.csdnimg.cn/20190107012324911.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

最后简要概括一下，获取锁的一个流程

![img](https://img-blog.csdnimg.cn/20190107012324996.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

 

**lock.unlock() 释放锁**

```java
public void unlock() {
    sync.release(1);
}
```

可以看到调用的是，**NonfairSync.release()**

![img](https://img-blog.csdnimg.cn/2019010701232524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

最后又调用了**NonfairSync.tryRelease()**

![img](https://img-blog.csdnimg.cn/2019010701232525.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

**基本可以确认，释放锁就是对AQS中的状态值State进行修改。同时更新下一个链表中的线程等待节点**。

 

 

**总结**

- lock的存储结构：一个int类型状态值（用于锁的状态变更），一个双向链表（用于存储等待中的线程）
- lock获取锁的过程：本质上是通过CAS来获取状态值修改，如果当场没获取到，会将该线程放在线程等待链表中。
- lock释放锁的过程：修改状态值，调整等待链表。

可以看到在整个实现过程中，lock大量使用CAS+自旋。因此根据CAS特性，lock建议使用在低锁冲突的情况下。目前java1.6以后，官方对synchronized做了大量的锁优化（偏向锁、自旋、轻量级锁）。因此在非必要的情况下，建议使用synchronized做同步操作。

最后，希望我的分析，能对你理解锁的实现有所帮助。

____________________________________________________________________________

**锁实现**

   简单说来，AbstractQueuedSynchronizer会把所有的请求线程构成一个CLH队列，当一个线程执行完毕（lock.unlock()）时会激活自己的后继节点，但正在执行的线程并不在队列中，而那些等待执行的线程全 部处于**阻塞状态**，经过调查线程的显式阻塞是通过调用LockSupport.park()完成，而LockSupport.park()则调用 sun.misc.Unsafe.park()本地方法，再进一步，HotSpot在Linux中中通过调用pthread_mutex_lock函数把 线程交给系统内核进行阻塞。

   与synchronized相同的是，这也是一个虚拟队列，不存在队列实例，仅存在节点之间的前后关系。令人疑惑的是为什么采用CLH队列呢？原生的CLH队列是用于自旋锁，但Doug Lea把其改造为阻塞锁。

   当有线程竞争锁时，该线程会首先尝试获得锁，这对于那些已经在队列中排队的线程来说显得不公平，这也是非公平锁的由来，与synchronized实现类似，这样会极大提高吞吐量。 如果已经存在Running线程，则新的竞争线程会被追加到队尾，具体是采用基于CAS的Lock-Free算法，因为线程并发对Tail调用CAS可能会 导致其他线程CAS失败，解决办法是循环CAS直至成功。AQS的实现非常精巧，令人叹为观止，不入细节难以完全领会其精髓，下面详细说明实现过程：

![img](https://img-blog.csdnimg.cn/2019010701232530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI5MzczMjg1,size_16,color_FFFFFF,t_70)

   AbstractQueuedSynchronizer通过构造一个基于阻塞的CLH队列容纳所有的阻塞线程，而对该队列的操作均通过Lock-Free（CAS）操作，但对已经获得锁的线程而言，ReentrantLock实现了偏向锁的功能。

synchronized 的底层也是一个基于CAS操作的等待队列，但JVM实现的更精细，把等待队列分为ContentionList和EntryList，目的是为了降低线程的出列速度；当然也实现了偏向锁，从数据结构来说二者设计没有本质区别。但synchronized还实现了自旋锁，并针对不同的系统和硬件体系进行了优 化，而Lock则完全依靠系统阻塞挂起等待线程。

当然Lock比synchronized更适合在应用层扩展，可以继承 AbstractQueuedSynchronizer定义各种实现，比如实现读写锁（ReadWriteLock），公平或不公平锁；同时，Lock对 应的Condition也比wait/notify要方便的多、灵活的多。

 

state值，若为0，意味着此时没有线程获取到资源

**简述总结：**

  总体来讲线程获取锁要经历以下过程(非公平)：

  1、调用lock方法，会先进行cas操作看下可否设置同步状态1成功，如果成功执行临界区代码

  2、如果不成功获取同步状态，如果状态是0那么cas设置为1.

  3、如果同步状态既不是0也不是自身线程持有会把当前线程构造成一个节点。

  4、把当前线程节点CAS的方式放入队列中，行为上线程阻塞，内部自旋获取状态。

   （acquireQueued的主要作用是把已经追加到队列的线程节点进行**阻塞**，但阻塞前又通过tryAccquire重试是否能获得锁，如果重试成功能则无需阻塞，直接返回。）

  5、线程释放锁，唤醒队列第一个节点，参与竞争。重复上述。

 

------

**synchronized和lock的底层区别\***

**synchronized的底层也是一个基于CAS操作的等待队列**，但JVM实现的更精细，把等待队列分为ContentionList和EntryList，目的是为了降低线程的出列速度；当然也实现了偏向锁，从数据结构来说二者设计没有本质区别。但synchronized还实现了**自旋锁**，并针对不同的系统和硬件体系进行了优化，而**Lock则完全依靠系统阻塞挂起等待线程。\****

 

当然Lock比synchronized更适合在应用层扩展，可以继承AbstractQueuedSynchronizer定义各种实现，比如实现读写锁（ReadWriteLock），公平或不公平锁；同时，Lock对应的Condition也比wait/notify要方便的多、灵活的多。

ReentrantLock是一个可重入的互斥锁，ReentrantLock由最近成功获取锁，还没有释放的线程所拥有

ReentrantLock与synchronized的区别

--ReentrantLock的lock机制有2种，忽略中断锁和响应中断锁

 

--synchronized实现的锁机制是可重入的，主要区别是中断控制和竞争锁公平策略

------

两者区别：

1.首先synchronized是java内置关键字，在jvm层面，Lock是个java类；

2.synchronized无法判断是否获取锁的状态，Lock可以判断是否获取到锁；

3.synchronized会自动释放锁(a 线程执行完同步代码会释放锁 ；b 线程执行过程中发生异常会释放锁)，Lock需在finally中手工释放锁（unlock()方法释放锁），否则容易造成线程死锁；

4.用synchronized关键字的两个线程1和线程2，如果当前线程1获得锁，线程2线程等待。如果线程1阻塞，线程2则会一直等待下去，而Lock锁就不一定会等待下去，如果尝试获取不到锁，线程可以不用一直等待就结束了；

5.synchronized的锁可重入、不可中断、非公平，而Lock锁可重入、可判断、可公平（两者皆可）

6.Lock锁适合大量同步的代码的同步问题，synchronized锁适合代码少量的同步问题。

 

**synchronized底层实现**

synchronized 属于重量级锁，效率低下，因为监视器锁（monitor）是依赖于底层操作系统的 Mutex Lock 来实现的，而操作系统实现线程之间的切换时需要从用户态转换到核心态，这个状态之间的转换需要相对比较长的时间，时间成本相对较高，这也是为什么早期的 synchronized 效率低的原因。庆幸的是在 Java 6 之后 Java 官方从 JVM 层面对 synchronized 进行了较大优化，所以现在的 synchronized 锁效率也优化得很不错了。Java 6 之后，**为了减少获得锁和释放锁所带来的性能消耗**，引入了轻量级锁和偏向锁，

 

**Lock底层实现**

Lock底层实现基于AQS实现，采用线程独占的方式，在硬件层面依赖特殊的CPU指令（CAS）。

简单来说，ReenTrantLock的实现是一种**自旋锁**，通过循环调用CAS操作来实现加锁。它的性能比较好也是因为**避免了使线程进入内核态的阻塞状态。**想尽办法避免线程进入内核的阻塞状态是我们去分析和理解锁设计的关键钥匙。

 

**volatile底层实现**

在JVM底层volatile是采用“**内存屏障**”来实现的。

 

lock和Monitor的区别

一、lock的底层本身是Monitor来实现的，所以Monitor可以实现lock的所有功能。

二、Monitor有TryEnter的功能，可以防止出现死锁的问题，lock没有。