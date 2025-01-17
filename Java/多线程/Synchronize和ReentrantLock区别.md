#### 目录介绍

- 1.Synchronize和ReentrantLock区别 
  - 1.1 相似点
  - 1.2 区别
  - 1.3 什么是线程安全问题？如何理解
  - 1.4 线程安全需要保证几个基本特性
- 2.Synchronize在编译时如何实现锁机制
- 3.ReentrantLock使用方法
- 4.ReentrantLock锁机制测试案例分析 
  - 4.1 代码案例分析
  - 4.2 什么时候选择用ReentrantLock
  - 4.3 公平锁和非公平锁有何区别
- 5.问答测试题 
  - 5.1 ReentrantLock和synchronized使用分析

### 好消息

- 博客笔记大汇总【16年3月到至今】，包括Java基础及深入知识点，Android技术博客，Python学习笔记等等，还包括平时开发中遇到的bug汇总，当然也在工作之余收集了大量的面试题，长期更新维护并且修正，持续完善……开源的文件是markdown格式的！同时也开源了生活博客，从12年起，积累共计47篇[近20万字]，转载请注明出处，谢谢！
- **链接地址：github.com/yangchong21…**
- 如果觉得好，可以star一下，谢谢！当然也欢迎提出建议，万事起于忽微，量变引起质变！

### 关于锁机制文章

- 01.Synchronize深入解析
  - Synchronize深入解析，sychonized method 和 synchonized代码块的效率问题
- 02.Synchronize和ReentrantLock区别
  - Synchronize和ReentrantLock区别，Synchronize在编译时如何实现锁机制，ReentrantLock锁机制测试案例分析，公平锁和非公平锁有何区别等等
- 03.死锁的发生，定位与修复
  - 死锁的概念和产生死锁的根本原因是什么？死锁的预防策略中资源有序分配策略是什么。死锁发生的场景，死锁的危害，出现死锁需要满足条件分析，如何预防死锁，如何定位死锁，以及死锁修复方案分析等等

### 1.Synchronize和ReentrantLock区别

#### 1.1 相似点：

- 这两种同步方式有很多相似之处，它们都是加锁方式同步，而且都是阻塞式的同步，也就是说当如果一个线程获得了对象锁，进入了同步块，其他访问该同步块的线程都必须阻塞在同步块外面等待，而进行线程阻塞和唤醒的代价是比较高的（操作系统需要在用户态与内核态之间来回切换，代价很高，不过可以通过对锁优化进行改善）。

#### 1.2 区别：

##### 1.2.1 API层面

- 这两种方式最大区别就是对于Synchronized来说，它是java语言的关键字，是原生语法层面的互斥，需要jvm实现。而ReentrantLock它是JDK 1.5之后提供的API层面的互斥锁，需要lock()和unlock()方法配合try/finally语句块来完成。

- synchronized既可以修饰方法，也可以修饰代码块。

  ```java
  //synchronized修饰一个方法时，这个方法叫同步方法。
  public synchronized void test() {
  //方法体``
  
  }
  
  synchronized（Object） {
  //括号中表示需要锁的对象.
  //线程执行的时候会对Object上锁
  }
  复制代码
  ```

- ReentrantLock使用

  ```java
  private ReentrantLock lock = new ReentrantLock();
  public void run() {
      lock.lock();
      try{
          for(int i=0;i<5;i++){
              System.out.println(Thread.currentThread().getName()+":"+i);
          }
      }finally{
          lock.unlock();
      }
  }
  复制代码
  ```

##### 1.2.2 等待可中断

- 等待可中断是指当持有锁的线程长期不释放锁的时候，正在等待的线程可以选择放弃等待，改为处理其他事情。可等待特性对处理执行时间非常长的同步快很有帮助。
- 具体来说，假如业务代码中有两个线程，Thread1 Thread2。假设 Thread1 获取了对象object的锁，Thread2将等待Thread1释放object的锁。 
  - 使用synchronized。如果Thread1不释放，Thread2将一直等待，不能被中断。synchronized也可以说是Java提供的原子性内置锁机制。内部锁扮演了互斥锁（mutual exclusion lock ，mutex）的角色，一个线程引用锁的时候，别的线程阻塞等待。
  - 使用ReentrantLock。如果Thread1不释放，Thread2等待了很长时间以后，可以中断等待，转而去做别的事情。

##### 1.2.3 公平锁

- 公平锁是指多个线程在等待同一个锁时，必须按照申请的时间顺序来依次获得锁；而非公平锁则不能保证这一点。非公平锁在锁被释放时，任何一个等待锁的线程都有机会获得锁。
- synchronized的锁是非公平锁，ReentrantLock默认情况下也是非公平锁，但可以通过带布尔值的构造函数要求使用公平锁。 
  - ReentrantLock 构造器的一个参数是boolean值，它允许您选择想要一个公平（fair）锁，还是一个不公平（unfair）锁。公平锁：使线程按照请求锁的顺序依次获得锁, 但是有成本;不公平锁：则允许讨价还价
  - 那么如何用代码设置公平锁呢？如下所示
  - ![image](https://user-gold-cdn.xitu.io/2018/10/18/16687054177950c6?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

##### 1.2.4 锁绑定多个条件

- ReentrantLock可以同时绑定多个Condition对象，只需多次调用newCondition方法即可。
- synchronized中，锁对象的wait()和notify()或notifyAll()方法可以实现一个隐含的条件。但如果要和多于一个的条件关联的时候，就不得不额外添加一个锁。

#### 1.3 什么是线程安全问题？如何理解

- 如果你的代码所在的进程中有多个线程在同时运行，而这些线程可能会同时运行这段代码。如果每次运行结果和单线程运行的结果是一样的，而且其他的变量的值也和预期的是一样的，就是线程安全的，或者说:一个类或者程序所提供的接口对于线程来说是原子操作或者多个线程之间的切换不会导致该接口的执行结果存在二义性,也就是说我们不用考虑同步的问题 。

#### 1.4 线程安全需要保证几个基本特性

- 1、原子性，简单说就是相关操作不会中途被其他线程干扰，一般通过同步机制实现。
- 2、可见性，是一个线程修改了某个共享变量，其状态能够立即被其他线程知晓，通常被解释为将线程本地状态反映到主内存上，volatile 就是负责保证可见性的。
- 3、有序性，是保证线程内串行语义，避免指令重排等。

### 2.Synchronize在编译时如何实现锁机制

- Synchronized进过编译，会在同步块的前后分别形成monitorenter和monitorexit这个两个字节码指令。在执行monitorenter指令时，首先要尝试获取对象锁。如果这个对象没被锁定，或者当前线程已经拥有了那个对象锁，把锁的计算器加1，相应的，在执行monitorexit指令时会将锁计算器就减1，当计算器为0时，锁就被释放了。如果获取对象锁失败，那当前线程就要阻塞，直到对象锁被另一个线程释放为止。

### 3.ReentrantLock使用方法

- ReentrantLock是java.util.concurrent包下提供的一套互斥锁，相比Synchronized，ReentrantLock类提供了一些高级功能，主要有以下3项： 

  - 1.等待可中断，持有锁的线程长期不释放的时候，正在等待的线程可以选择放弃等待，这相当于Synchronized来说可以避免出现死锁的情况。
  - 2.公平锁，多个线程等待同一个锁时，必须按照申请锁的时间顺序获得锁，Synchronized锁非公平锁，ReentrantLock默认的构造函数是创建的非公平锁，可以通过参数true设为公平锁，但公平锁表现的性能不是很好。
  - 3.锁绑定多个条件，一个ReentrantLock对象可以同时绑定对个对象。

- 使用方法代码如下

  ```java
  private ReentrantLock lock = new ReentrantLock();
  public void run() {
      lock.lock();
      try{
          for(int i=0;i<5;i++){
              System.out.println(Thread.currentThread().getName()+":"+i);
          }
      }finally{
          lock.unlock();
      }
  }
  ```
  
- 注意问题：为保证锁释放，每一个 lock() 动作，建议都立即对应一都立即对应一个 try-catch-finally

### 4.ReentrantLock锁机制测试案例分析

#### 4.1 代码案例分析

- 代码如下所示

  ```java
  private void test2() {
      Runnable t1 = new MyThread();
      new Thread(t1,"t1").start();
      new Thread(t1,"t2").start();
  }
  
  class MyThread implements Runnable {
      private ReentrantLock lock = new ReentrantLock();
      public void run() {
          lock.lock();
          try{
              for(int i=0;i<5;i++){
                  System.out.println(Thread.currentThread().getName()+":"+i);
              }
          }finally{
              lock.unlock();
          }
      }
  }
  
  //打印值如下所示
  10-17 17:06:59.222 6531-6846/com.yc.cn.ycbaseadapter I/System.out: t1:0
  10-17 17:06:59.222 6531-6846/com.yc.cn.ycbaseadapter I/System.out: t1:1
  10-17 17:06:59.222 6531-6846/com.yc.cn.ycbaseadapter I/System.out: t1:2
  10-17 17:06:59.222 6531-6846/com.yc.cn.ycbaseadapter I/System.out: t1:3
  10-17 17:06:59.222 6531-6846/com.yc.cn.ycbaseadapter I/System.out: t1:4
  10-17 17:06:59.224 6531-6847/com.yc.cn.ycbaseadapter I/System.out: t2:0
  10-17 17:06:59.225 6531-6847/com.yc.cn.ycbaseadapter I/System.out: t2:1
  10-17 17:06:59.225 6531-6847/com.yc.cn.ycbaseadapter I/System.out: t2:2
  10-17 17:06:59.225 6531-6847/com.yc.cn.ycbaseadapter I/System.out: t2:3
  10-17 17:06:59.225 6531-6847/com.yc.cn.ycbaseadapter I/System.out: t2:4
  复制代码
  ```

#### 4.2 什么时候选择用ReentrantLock

- 适用场景：时间锁等候、可中断锁等候、无块结构锁、多个条件变量或者锁投票

- 在确实需要一些 synchronized所没有的特性的时候，比如时间锁等候、可中断锁等候、无块结构锁、多个条件变量或者锁投票。 ReentrantLock 还具有可伸缩性的好处，应当在高度争用的情况下使用它，但是请记住，大多数 synchronized 块几乎从来没有出现过争用，所以可以把高度争用放在一边。我建议用 synchronized 开发，直到确实证明 synchronized 不合适，而不要仅仅是假设如果使用 ReentrantLock “性能会更好”。请记住，这些是供高级用户使用的高级工具。（而且，真正的高级用户喜欢选择能够找到的最简单工具，直到他们认为简单的工具不适用为止。）。一如既往，首先要把事情做好，然后再考虑是不是有必要做得更快。

- 使用场景代码展示【摘自ThreadPoolExecutor类，这个类中很多地方用到了这个锁。自己可以查看】：

  ```
  /**
   * Rolls back the worker thread creation.
   * - removes worker from workers, if present
   * - decrements worker count
   * - rechecks for termination, in case the existence of this
   *   worker was holding up termination
   */
  private void addWorkerFailed(Worker w) {
      final ReentrantLock mainLock = this.mainLock;
      mainLock.lock();
      try {
          if (w != null)
              workers.remove(w);
          decrementWorkerCount();
          tryTerminate();
      } finally {
          mainLock.unlock();
      }
  }
  复制代码
  ```

#### 4.3 公平锁和非公平锁有何区别

- 公平性是指在竞争场景中，当公平性为真时，会倾向于将锁赋予等待时间最久的线程。公平性是减少线程“饥饿”（个别线程长期等待锁，但始终无法获取）情况发生的一个办法。 

  - 1、公平锁能保证：老的线程排队使用锁，新线程仍然排队使用锁。
  - 2、非公平锁保证：老的线程排队使用锁；但是无法保证新线程抢占已经在排队的线程的锁。
  - 看下面代码案例所示：可以得出结论，公平锁指的是哪个线程先运行，那就可以先得到锁。非公平锁是不管线程是否是先运行，新的线程都有可能抢占已经在排队的线程的锁。

  ```java
  private void test3() {
      Service service = new Service();
      ThreadClass tcArray[] = new ThreadClass[10];
      for(int i=0;i<10;i++){
          tcArray[i] = new ThreadClass(service);
          tcArray[i].start();
      }
  }
  
  public class Service {
      ReentrantLock lock = new ReentrantLock(true);
      Service() {
      }
  
      void getThreadName() {
          System.out.println(Thread.currentThread().getName() + " 已经被锁定");
      }
  }
  public class ThreadClass extends Thread{
      private Service service;
      ThreadClass(Service service) {
          this.service = service;
      }
      public void run(){
          System.out.println(Thread.currentThread().getName() + " 抢到了锁");
          service.lock.lock();
          service.getThreadName();
          service.lock.unlock();
      }
  }
  //当ReentrantLock设置true，也就是公平锁时
  10-17 19:32:22.422 6459-6523/com.yc.cn.ycbaseadapter I/System.out: Thread-5 抢到了锁
  10-17 19:32:22.422 6459-6523/com.yc.cn.ycbaseadapter I/System.out: Thread-5 已经被锁定
  10-17 19:32:22.424 6459-6524/com.yc.cn.ycbaseadapter I/System.out: Thread-6 抢到了锁
  10-17 19:32:22.424 6459-6524/com.yc.cn.ycbaseadapter I/System.out: Thread-6 已经被锁定
  10-17 19:32:22.427 6459-6525/com.yc.cn.ycbaseadapter I/System.out: Thread-7 抢到了锁
  10-17 19:32:22.427 6459-6526/com.yc.cn.ycbaseadapter I/System.out: Thread-8 抢到了锁
  10-17 19:32:22.427 6459-6525/com.yc.cn.ycbaseadapter I/System.out: Thread-7 已经被锁定
  10-17 19:32:22.427 6459-6526/com.yc.cn.ycbaseadapter I/System.out: Thread-8 已经被锁定
  10-17 19:32:22.427 6459-6527/com.yc.cn.ycbaseadapter I/System.out: Thread-9 抢到了锁
  10-17 19:32:22.427 6459-6527/com.yc.cn.ycbaseadapter I/System.out: Thread-9 已经被锁定
  10-17 19:32:22.428 6459-6528/com.yc.cn.ycbaseadapter I/System.out: Thread-10 抢到了锁
  10-17 19:32:22.428 6459-6528/com.yc.cn.ycbaseadapter I/System.out: Thread-10 已经被锁定
  10-17 19:32:22.429 6459-6529/com.yc.cn.ycbaseadapter I/System.out: Thread-11 抢到了锁
  10-17 19:32:22.429 6459-6529/com.yc.cn.ycbaseadapter I/System.out: Thread-11 已经被锁定
  10-17 19:32:22.430 6459-6530/com.yc.cn.ycbaseadapter I/System.out: Thread-12 抢到了锁
  10-17 19:32:22.430 6459-6530/com.yc.cn.ycbaseadapter I/System.out: Thread-12 已经被锁定
  10-17 19:32:22.431 6459-6532/com.yc.cn.ycbaseadapter I/System.out: Thread-14 抢到了锁
  10-17 19:32:22.431 6459-6532/com.yc.cn.ycbaseadapter I/System.out: Thread-14 已经被锁定
  10-17 19:32:22.432 6459-6531/com.yc.cn.ycbaseadapter I/System.out: Thread-13 抢到了锁
  10-17 19:32:22.433 6459-6531/com.yc.cn.ycbaseadapter I/System.out: Thread-13 已经被锁定
  
  
  //当ReentrantLock设置false，也就是非公平锁时
  10-17 19:34:58.102 7089-7183/com.yc.cn.ycbaseadapter I/System.out: Thread-5 抢到了锁
  10-17 19:34:58.102 7089-7184/com.yc.cn.ycbaseadapter I/System.out: Thread-6 抢到了锁
  10-17 19:34:58.103 7089-7183/com.yc.cn.ycbaseadapter I/System.out: Thread-5 已经被锁定
  10-17 19:34:58.103 7089-7185/com.yc.cn.ycbaseadapter I/System.out: Thread-7 抢到了锁
  10-17 19:34:58.103 7089-7185/com.yc.cn.ycbaseadapter I/System.out: Thread-7 已经被锁定
  10-17 19:34:58.103 7089-7184/com.yc.cn.ycbaseadapter I/System.out: Thread-6 已经被锁定
  10-17 19:34:58.104 7089-7186/com.yc.cn.ycbaseadapter I/System.out: Thread-8 抢到了锁
  10-17 19:34:58.105 7089-7186/com.yc.cn.ycbaseadapter I/System.out: Thread-8 已经被锁定
  10-17 19:34:58.108 7089-7187/com.yc.cn.ycbaseadapter I/System.out: Thread-9 抢到了锁
  10-17 19:34:58.108 7089-7187/com.yc.cn.ycbaseadapter I/System.out: Thread-9 已经被锁定
  10-17 19:34:58.111 7089-7188/com.yc.cn.ycbaseadapter I/System.out: Thread-10 抢到了锁
  10-17 19:34:58.112 7089-7188/com.yc.cn.ycbaseadapter I/System.out: Thread-10 已经被锁定
  10-17 19:34:58.112 7089-7189/com.yc.cn.ycbaseadapter I/System.out: Thread-11 抢到了锁
  10-17 19:34:58.113 7089-7189/com.yc.cn.ycbaseadapter I/System.out: Thread-11 已经被锁定
  10-17 19:34:58.113 7089-7193/com.yc.cn.ycbaseadapter I/System.out: Thread-14 抢到了锁
  10-17 19:34:58.113 7089-7193/com.yc.cn.ycbaseadapter I/System.out: Thread-14 已经被锁定
  10-17 19:34:58.115 7089-7190/com.yc.cn.ycbaseadapter I/System.out: Thread-12 抢到了锁
  10-17 19:34:58.115 7089-7190/com.yc.cn.ycbaseadapter I/System.out: Thread-12 已经被锁定
  10-17 19:34:58.116 7089-7191/com.yc.cn.ycbaseadapter I/System.out: Thread-13 抢到了锁
  10-17 19:34:58.116 7089-7191/com.yc.cn.ycbaseadapter I/System.out: Thread-13 已经被锁定
  ```

### 5.问答测试题

#### 5.1 ReentrantLock和synchronized使用分析

- ReentrantLock是Lock的实现类，是一个互斥的同步器，在多线程高竞争条件下，ReentrantLock比synchronized有更加优异的性能表现。
- 1 用法比较 
  - Lock使用起来比较灵活，但是必须有释放锁的配合动作
  - Lock必须手动获取与释放锁，而synchronized不需要手动释放和开启锁
  - Lock只适用于代码块锁，而synchronized可用于修饰方法、代码块等
- 2 特性比较 
  - ReentrantLock的优势体现在： 
    - 具备尝试非阻塞地获取锁的特性：当前线程尝试获取锁，如果这一时刻锁没有被其他线程获取到，则成功获取并持有锁
    - 能被中断地获取锁的特性：与synchronized不同，获取到锁的线程能够响应中断，当获取到锁的线程被中断时，中断异常将会被抛出，同时锁会被释放
    - 超时获取锁的特性：在指定的时间范围内获取锁；如果截止时间到了仍然无法获取锁，则返回
- 3 注意事项 
  - 在使用ReentrantLock类的时，一定要注意三点： 
    - 在finally中释放锁，目的是保证在获取锁之后，最终能够被释放
    - 不要将获取锁的过程写在try块内，因为如果在获取锁时发生了异常，异常抛出的同时，也会导致锁无故被释放。
    - ReentrantLock提供了一个newCondition的方法，以便用户在同一锁的情况下可以根据不同的情况执行等待或唤醒的动作。

