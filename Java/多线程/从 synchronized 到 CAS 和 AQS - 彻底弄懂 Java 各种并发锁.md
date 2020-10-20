# 概述

Java 中的并发锁大致分为隐式锁和显式锁两种。隐式锁就是我们最常使用的 synchronized 关键字，显式锁主要包含两个接口：Lock 和 ReadWriteLock，主要实现类分别为 ReentrantLock 和 ReentrantReadWriteLock，这两个类都是基于 AQS(AbstractQueuedSynchronizer) 实现的。还有的地方将 CAS 也称为一种锁，在包括 AQS 在内的很多并发相关类中，CAS 都扮演了很重要的角色。

我们只需要弄清楚 synchronized 和 AQS 的原理，再去理解并发锁的性质和局限就很简单了。因此这篇文章重点放在原理上，对于使用和特点不会过多涉及。

# 概念辨析

下面是关于锁的一些概念解释，这些都是一些关于锁的性质的描述，并非具体实现。

## 悲观锁和乐观锁

悲观锁和独占锁是一个意思，它假设一定会发生冲突，因此获取到锁之后会阻塞其他等待线程。这么做的好处是简单安全，但是挂起线程和恢复线程都需要转入内核态进行，这样做会带来很大的性能开销。悲观锁的代表是 synchronized。然而在真实环境中，大部分时候都不会产生冲突。悲观锁会造成很大的浪费。而乐观锁不一样，它假设不会产生冲突，先去尝试执行某项操作，失败了再进行其他处理（一般都是不断循环重试）。这种锁不会阻塞其他的线程，也不涉及上下文切换，性能开销小。代表实现是 CAS。

## 公平锁和非公平锁

公平锁是指各个线程在加锁前先检查有无排队的线程，按排队顺序去获得锁。 非公平锁是指线程加锁前不考虑排队问题，直接尝试获取锁，获取不到再去队尾排队。值得注意的是，在 AQS 的实现中，一旦线程进入排队队列，即使是非公平锁，线程也得乖乖排队。

## 可重入锁和不可重入锁

如果一个线程已经获取到了一个锁，那么它可以访问被这个锁锁住的所有代码块。不可重入锁与之相反。

# Synchronized 关键字

Synchronized 是一种独占锁。在修饰静态方法时，锁的是类对象，如 Object.class。修饰非静态方法时，锁的是对象，即 this。修饰方法块时，锁的是括号里的对象。 每个对象有一个锁和一个等待队列，锁只能被一个线程持有，其他需要锁的线程需要阻塞等待。锁被释放后，对象会从队列中取出一个并唤醒，唤醒哪个线程是不确定的，不保证公平性。

## 类锁与对象锁

synchronized 修饰静态方法时，锁的是类对象,如 Object.class。修饰非静态方法时，锁的是对象，即 this。 多个线程是可以同时执行同一个synchronized实例方法的，只要它们访问的对象是不同的。

synchronized 锁住的是对象而非代码，只要访问的是同一个对象的 synchronized 方法，即使是不同的代码，也会被同步顺序访问。

此外，需要说明的，synchronized方法不能防止非synchronized方法被同时执行，所以，一般在保护变量时，需要在所有访问该变量的方法上加上synchronized。

## 实现原理

synchronized 是基于 Java 对象头和 Monitor 机制来实现的。

### Java 对象头

一个对象在内存中包含三部分：对象头，实例数据和对齐填充。其中 Java 对象头包含两部分：

- Class Metadata Address （类型指针）。存储类的元数据的指针。虚拟机通过这个指针找到它是哪个类的实例。
- Mark Word（标记字段）。存出一些对象自身运行时的数据。包括哈希码，GC 分代年龄，锁状态标志等。

### Monitor

Mark Word 有一个字段指向 monitor 对象。monitor 中记录了锁的持有线程，等待的线程队列等信息。前面说的每个对象都有一个锁和一个等待队列，就是在这里实现的。 monitor 对象由 C++ 实现。其中有三个关键字段：

- _owner 记录当前持有锁的线程
- _EntryList 是一个队列，记录所有阻塞等待锁的线程
- _WaitSet 也是一个队列，记录调用 wait() 方法并还未被通知的线程。

Monitor的操作机制如下：

1. 多个线程竞争锁时，会先进入 EntryList 队列。竞争成功的线程被标记为 Owner。其他线程继续在此队列中阻塞等待。
2. 如果 Owner 线程调用 wait() 方法，则其释放对象锁并进入 WaitSet 中等待被唤醒。Owner 被置空，EntryList 中的线程再次竞争锁。
3. 如果 Owner 线程执行完了，便会释放锁，Owner 被置空，EntryList 中的线程再次竞争锁。

### JVM 对 synchronized 的处理

上面了解了 monitor 的机制，那虚拟机是如何将 synchronized 和 monitor 关联起来的呢？分两种情况：

- 如果同步的是代码块，编译时会直接在同步代码块前加上 monitorenter 指令，代码块后加上 monitorexit 指令。这称为显示同步。
- 如果同步的是方法，虚拟机会为方法设置 ACC_SYNCHRONIZED 标志。调用的时候 JVM 根据这个标志判断是否是同步方法。

## JVM 对 synchronized 的优化

synchronized 是重量级锁，由于消耗太大，虚拟机对其做了一些优化。

### 自旋锁与自适应自旋

在许多应用中，锁定状态只会持续很短的时间，为了这么一点时间去挂起恢复线程，不值得。我们可以让等待线程执行一定次数的循环，在循环中去获取锁。这项技术称为自旋锁，它可以节省系统切换线程的消耗，但仍然要占用处理器。在 JDK1.4.2 中，自选的次数可以通过参数来控制。 JDK 1.6又引入了自适应的自旋锁，不再通过次数来限制，而是由前一次在同一个锁上的自旋时间及锁的拥有者的状态来决定。

### 锁消除

虚拟机在运行时，如果发现一段被锁住的代码中不可能存在共享数据，就会将这个锁清除。

### 锁粗化

当虚拟机检测到有一串零碎的操作都对同一个对象加锁时，会把锁扩展到整个操作序列外部。如 StringBuffer 的 append 操作。

### 轻量级锁

对绝大部分的锁来说，在整个同步周期内都不存在竞争。如果没有竞争，轻量级锁可以使用 CAS 操作避免使用互斥量的开销。

### 偏向锁

偏向锁的核心思想是，如果一个线程获得了锁，那么锁就进入偏向模式，当这个线程再次请求锁时，无需再做任何同步操作，即可获取锁。

# CAS

## 操作模型

CAS 是 compare and swap 的简写，即比较并交换。它是指一种操作机制，而不是某个具体的类或方法。在 Java 平台上对这种操作进行了包装。在 Unsafe 类中，调用代码如下：

```
unsafe.compareAndSwapInt(this, valueOffset, expect, update);
复制代码
```

它需要三个参数，分别是内存位置 V，旧的预期值 A 和新的值 B。操作时，先从内存位置读取到值，然后和预期值A比较。如果相等，则将此内存位置的值改为新值 B，返回 true。如果不相等，说明和其他线程冲突了，则不做任何改变，返回 false。

这种机制在不阻塞其他线程的情况下避免了并发冲突，比独占锁的性能高很多。 CAS 在 Java 的原子类和并发包中有大量使用。

## 重试机制（循环 CAS）

**有很多文章说，CAS 操作失败后会一直重试直到成功，这种说法很不严谨。**

第一，CAS 本身并未实现失败后的处理机制，它只负责返回成功或失败的布尔值，后续由调用者自行处理。只不过我们最常用的处理方式是重试而已。

第二，这句话很容易理解错，被理解成重新比较并交换。实际上失败的时候，原值已经被修改，如果不更改期望值，再怎么比较都会失败。而新值同样需要修改。

所以正确的方法是，使用一个死循环进行 CAS 操作，成功了就结束循环返回，失败了就重新从内存读取值和计算新值，再调用 CAS。看下 AtomicInteger 的源码就什么都懂了：

```
public final int incrementAndGet () {
    for (;;) {
        int current = get();
        int next = current + 1;
        if (compareAndSet(current, next))
            return next;
    }
}
复制代码
```

## 底层实现

CAS 主要分三步，读取-比较-修改。其中比较是在检测是否有冲突，如果检测到没有冲突后，其他线程还能修改这个值，那么 CAS 还是无法保证正确性。所以最关键的是要保证比较-修改这两步操作的原子性。

CAS 底层是靠调用 CPU 指令集的 cmpxchg 完成的，它是 x86 和 Intel 架构中的 compare and exchange 指令。在多核的情况下，这个指令也不能保证原子性，需要在前面加上  lock 指令。lock 指令可以保证一个 CPU 核心在操作期间独占一片内存区域。那么 这又是如何实现的呢？

在处理器中，一般有两种方式来实现上述效果：总线锁和缓存锁。在多核处理器的结构中，CPU 核心并不能直接访问内存，而是统一通过一条总线访问。总线锁就是锁住这条总线，使其他核心无法访问内存。这种方式代价太大了，会导致其他核心停止工作。而缓存锁并不锁定总线，只是锁定某部分内存区域。当一个 CPU 核心将内存区域的数据读取到自己的缓存区后，它会锁定缓存对应的内存区域。锁住期间，其他核心无法操作这块内存区域。

CAS 就是通过这种方式实现比较和交换操作的原子性的。**值得注意的是， CAS 只是保证了操作的原子性，并不保证变量的可见性，因此变量需要加上 volatile 关键字。**

## ABA 问题

上面提到，CAS 保证了比较和交换的原子性。但是从读取到开始比较这段期间，其他核心仍然是可以修改这个值的。如果核心将 A 修改为 B，CAS 可以判断出来。但是如果核心将 A 修改为 B 再修改回 A。那么 CAS 会认为这个值并没有被改变，从而继续操作。这是和实际情况不符的。解决方案是加一个版本号。

# 可重入锁 ReentrantLock

ReentrantLock 使用代码实现了和 synchronized 一样的语义，包括可重入，保证内存可见性和解决竞态条件问题等。相比 synchronized，它还有如下好处：

- 支持以非阻塞方式获取锁
- 可以响应中断
- 可以限时
- 支持了公平锁和非公平锁

基本用法如下：

```
public class Counter {
    private final Lock lock = new ReentrantLock();
    private volatile int count;

    public void incr() {
        lock.lock();
        try {
            count++;
        } finally {
            lock.unlock();
        }
    }

    public int getCount() {
        return count;
    }
}
复制代码
```

ReentrantLock 内部有两个内部类，分别是 FairSync 和 NoFairSync，对应公平锁和非公平锁。他们都继承自 Sync。Sync 又继承自AQS。

# AQS

AQS 全称 AbstractQueuedSynchronizer。AQS 中有两个重要的成员：

- 成员变量 state。用于表示锁现在的状态，用 volatile 修饰，保证内存一致性。同时所用对 state 的操作都是使用 CAS 进行的。state 为0表示没有任何线程持有这个锁，线程持有该锁后将 state 加1，释放时减1。多次持有释放则多次加减。
- 还有一个双向链表，链表除了头结点外，每一个节点都记录了线程的信息，代表一个等待线程。这是一个 FIFO 的链表。

下面以 ReentrantLock 非公平锁的代码看看 AQS 的原理。

## 请求锁

请求锁时有三种可能：

1. 如果没有线程持有锁，则请求成功，当前线程直接获取到锁。
2. 如果当前线程已经持有锁，则使用 CAS 将 state 值加1，表示自己再次申请了锁，释放锁时减1。这就是可重入性的实现。
3. 如果由其他线程持有锁，那么将自己添加进等待队列。

```
final void lock() {
    if (compareAndSetState(0, 1))   
        setExclusiveOwnerThread(Thread.currentThread()); //没有线程持有锁时，直接获取锁，对应情况1
    else
        acquire(1);
}

public final void acquire(int arg) {
    if (!tryAcquire(arg) && //在此方法中会判断当前持有线程是否等于自己，对应情况2
        acquireQueued(addWaiter(Node.EXCLUSIVE), arg)) //将自己加入队列中，对应情况3
        selfInterrupt();
}
复制代码
```

## 创建 Node 节点并加入链表

如果没竞争到锁，这时候就要进入等待队列。队列是默认有一个 head 节点的，并且不包含线程信息。上面情况3中，addWaiter 会创建一个 Node，并添加到链表的末尾，Node 中持有当前线程的引用。同时还有一个成员变量 waitStatus，表示线程的等待状态，初始值为0。我们还需要关注两个值：

- CANCELLED，值为1，表示取消状态，就是说我不要这个锁了，请你把我移出去。
- SINGAL，值为-1，表示下一个节点正在挂起等待，注意是下一个节点，不是当前节点。

同时，加到链表末尾的操作使用了 CAS+死循环的模式，很有代表性，拿出来看一看：

```java
Node node = new Node(mode);
for (;;) {
    Node oldTail = tail;
    if (oldTail != null) {
        U.putObject(node, Node.PREV, oldTail);
        if (compareAndSetTail(oldTail, node)) {
            oldTail.next = node;
            return node;
        }
    } else {
        initializeSyncQueue();
    }
}
复制代码
```

可以看到，在死循环里调用了 CAS 的方法。如果多个线程同时调用该方法，那么每次循环都只有一个线程执行成功，其他线程进入下一次循环，重新调用。N个线程就会循环N次。这样就在无锁的模式下实现了并发模型。

## 挂起等待

- 如果此节点的上一个节点是头部节点，则再次尝试获取锁，获取到了就移除并返回。获取不到就进入下一步；
- 判断前一个节点的 waitStatus，如果是 SINGAL，则返回 true，并调用 LockSupport.park() 将线程挂起；
- 如果是 CANCELLED，则将前一个节点移除；
- 如果是其他值，则将前一个节点的 waitStatus 标记为 SINGAL，进入下一次循环。

可以看到，一个线程最多有两次机会，还竞争不到就去挂起等待。

```java
final boolean acquireQueued(final Node node, int arg) {
    try {
        boolean interrupted = false;
        for (;;) {
            final Node p = node.predecessor();
            if (p == head && tryAcquire(arg)) {
                setHead(node);
                p.next = null; // help GC
                return interrupted;
            }
            if (shouldParkAfterFailedAcquire(p, node) &&
                parkAndCheckInterrupt())
                interrupted = true;
        }
    } catch (Throwable t) {
        cancelAcquire(node);
        throw t;
    }
}
```

## 释放锁

- 调用 tryRelease，此方法由子类实现。实现非常简单，如果当前线程是持有锁的线程，就将 state 减1。减完后如果 state 大于0，表示当前线程仍然持有锁，返回 false。如果等于0，表示已经没有线程持有锁，返回 true，进入下一步；
- 如果头部节点的 waitStatus 不等于0，则调用LockSupport.unpark()唤醒其下一个节点。头部节点的下一个节点就是等待队列中的第一个线程，这反映了 AQS 先进先出的特点。另外，即使是非公平锁，进入队列之后，还是得按顺序来。

```java
public final boolean release(int arg) {
    if (tryRelease(arg)) { //将 state 减1
        Node h = head;
        if (h != null && h.waitStatus != 0)
            unparkSuccessor(h);
        return true;
    }
    return false;
}

private void unparkSuccessor(Node node) {
    int ws = node.waitStatus;
    if (ws < 0)
        node.compareAndSetWaitStatus(ws, 0);
        
    Node s = node.next;
    if (s == null || s.waitStatus > 0) { 
        s = null;
        for (Node p = tail; p != node && p != null; p = p.prev)
            if (p.waitStatus <= 0)
                s = p;
    }
    if (s != null) //唤醒第一个等待的线程
        LockSupport.unpark(s.thread);
}
复制代码
```

## 公平锁如何实现

上面分析的是非公平锁，那公平锁呢？很简单，在竞争锁之前判断一下等待队列中有没有线程在等待就行了。

```java
protected final boolean tryAcquire(int acquires) {
    final Thread current = Thread.currentThread();
    int c = getState();
    if (c == 0) {
        if (!hasQueuedPredecessors() && //判断等待队列是否有节点
            compareAndSetState(0, acquires)) {
            setExclusiveOwnerThread(current);
            return true;
        }
    }
    ......
    return false;
}
复制代码
```

# 可重入读写锁 ReentrantReadWriteLock

## 读写锁机制

理解 ReentrantLock 和 AQS 之后，再来理解读写锁就很简单了。读写锁有一个读锁和一个写锁，分别对应读操作和锁操作。锁的特性如下：

- 只有一个线程可以获取到写锁。在获取写锁时，只有没有任何线程持有任何锁才能获取成功；
- 如果有线程正持有写锁，其他任何线程都获取不到任何锁；
- 没有线程持有写锁时，可以有多个线程获取到读锁。

上面锁的特点保证了可以并发读取，这大大提高了效率，在实际开发中非常有用。那么在具体是如何实现的呢？

## 实现原理

读写锁虽然有两个锁，但实际上只有一个等待队列。

- 获取写锁时，要保证没有任何线程持有锁；
- 写锁释放后，会唤醒队列第一个线程，可能是读锁和写锁；
- 获取读锁时，先判断写锁有没有被持有，没有就可以获取成功；
- 获取读锁成功后，会将队列中等待读锁的线程挨个唤醒，知道遇到等待写锁的线程位置；
- 释放读锁时，要检查读锁数，如果为0，则唤醒队列中的下一个线程，否则不进行操作。


作者：Tree1916链接：https://juejin.im/post/6844903759047294983来源：掘金著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。