原文地址：[Difference between Wait and Sleep, Yield in Java](https://link.jianshu.com?t=http%3A%2F%2Fjavarevisited.blogspot.com%2F2011%2F12%2Fdifference-between-wait-sleep-yield.html)

Java中wait、sleep的区别或者Java中sleep、yield的区别是Java面试或者多线程面试中最常问的问题之一。在这3个在Java中能够用来暂停线程的方法中，sleep()和yield()方法是定义在Thread类中，而wait()方法是定义在Object类中的， 这也是面试中常问的一个问题。

wait()和sleep()的关键的区别在于，wait()是用于线程间通信的，而sleep()是用于短时间暂停当前线程。更加明显的一个区别在于，当一个线程调用wait()方法的时候，会释放它锁持有的对象的管程和锁，但是调用sleep()方法的时候，不会释放他所持有的管程。

回到yield()方法上来，与wait()和sleep()方法有一些区别，它仅仅释放线程所占有的CPU资源，从而让其他线程有机会运行，但是并不能保证某个特定的线程能够获得CPU资源。谁能获得CPU完全取决于调度器，在有些情况下调用yield方法的线程甚至会再次得到CPU资源。所以，依赖于yield方法是不可靠的，它只能尽力而为。

## Wait vs Sleep vs Yield in Java

### Java中wait和sleep的区别

wait和sleep的主要区别是调用wait方法时，线程在等待的时候会释放掉它所获得的monitor，但是调用Thread.sleep()方法时，线程在等待的时候仍然会持有monitor或者锁。另外，Java中的wait方法应在同步代码块中调用，但是sleep方法不需要。
 另一个区别是Thread.sleep()方法是一个静态方法，作用在当前线程上；但是wait方法是一个实例方法，并且只能在其他线程调用本实例的notify()方法时被唤醒。另外，使用sleep方法时，被暂停的线程在被唤醒之后会立即进入就绪态（Runnable state)，但是使用wait方法的时候，被暂停的线程会首先获得锁（译者注：阻塞态），然后再进入就绪态。所以，根据你的需求，如果你需要暂定你的线程一段特定的时间就使用sleep()方法，如果你想要实现线程间通信就使用wait()方法。
 下面列出Java中wait和sleep方法的区别：

1. wait只能在同步（synchronize）环境中被调用，而sleep不需要。详见[Why to wait and notify needs to call from synchronized method](https://link.jianshu.com?t=http%3A%2F%2Fjavarevisited.blogspot.com%2F2011%2F05%2Fwait-notify-and-notifyall-in-java.html) 
2. 进入wait状态的线程能够被notify和notifyAll线程唤醒，但是进入sleeping状态的线程不能被notify方法唤醒。
3. wait通常有条件地执行，线程会一直处于wait状态，直到某个条件变为真。但是sleep仅仅让你的线程进入睡眠状态。
4. wait方法在进入wait状态的时候会释放对象的锁，但是sleep方法不会。
5. wait方法是针对一个被同步代码块加锁的对象，而sleep是针对一个线程。更详细的讲解可以参考《Java核心技术卷1》，里面介绍了如何使用wait和notify方法。

### yield和sleep的区别

yield和sleep的主要是，yield方法会临时暂停当前正在执行的线程，来让有同样优先级的正在等待的线程有机会执行。如果没有正在等待的线程，或者所有正在等待的线程的优先级都比较低，那么该线程会继续运行。执行了yield方法的线程什么时候会继续运行由线程调度器来决定，不同的厂商可能有不同的行为。yield方法不保证当前的线程会暂停或者停止，但是可以保证当前线程在调用yield方法时会放弃CPU。
 在Java中Sleep方法有两个， 一个只有一个毫秒参数，另一个有毫秒和纳秒两个参数。



```cpp
sleep(long millis)
```

or



```cpp
sleep(long millis, int nanos)
```

会让当前执行的线程sleep指定的时间。

下面这张图很好地展示了在调用wait、sleep、yield方法的时候，线程状态如何转换。



![img](https:////upload-images.jianshu.io/upload_images/66827-780462c52b8f5a83.png)

Paste_Image.png

Java中sleep方法的几个注意点：

1. Thread.sleep()方法用来暂停线程的执行，将CPU放给线程调度器。
2. Thread.sleep()方法是一个静态方法，它暂停的是当前执行的线程。
3. Java有两种sleep方法，一个只有一个毫秒参数，另一个有毫秒和纳秒两个参数。
4. 与wait方法不同，sleep方法不会释放锁
5. 如果其他的线程中断了一个休眠的线程，sleep方法会抛出Interrupted Exception。
6. 休眠的线程在唤醒之后不保证能获取到CPU，它会先进入就绪态，与其他线程竞争CPU。
7. 有一个易错的地方，当调用t.sleep()的时候，会暂停线程t。这是不对的，因为Thread.sleep是一个静态方法，它会使当前线程而不是线程t进入休眠状态。

这就是java中的sleep方法。我们已经看到了java中sleep、wait以及yield方法的区别。总之，记住sleep和yield作用于当前线程。

------

