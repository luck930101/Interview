Java 给多线程编程提供了内置的支持。 一条线程指的是进程中一个单一顺序的控制流，一个进程中可以并发多个线程，每条线程并行执行不同的任务。

多线程是多任务的一种特别的形式，但多线程使用了更小的资源开销。

这里定义和线程相关的另一个术语 - 进程：一个进程包括由操作系统分配的内存空间，包含一个或多个线程。一个线程不能独立的存在，它必须是进程的一部分。一个进程一直运行，直到所有的非守护线程都结束运行后才能结束。

多线程能满足程序员编写高效率的程序来达到充分利用 CPU 的目的。

------

# 1. 一个线程的生命周期

线程是一个动态执行的过程，它也有一个从产生到死亡的过程。

下图显示了一个线程完整的生命周期。

![img](https://www.runoob.com/wp-content/uploads/2014/01/java-thread.jpg)

- 新建状态:

  使用 **new** 关键字和 **Thread** 类或其子类建立一个线程对象后，该线程对象就处于新建状态。它保持这个状态直到程序 **start()** 这个线程。

- 就绪状态:

  当线程对象调用了start()方法之后，该线程就进入就绪状态。就绪状态的线程处于就绪队列中，要等待JVM里线程调度器的调度。

- 运行状态:

  如果就绪状态的线程获取 CPU 资源，就可以执行 **run()**，此时线程便处于运行状态。处于运行状态的线程最为复杂，它可以变为阻塞状态、就绪状态和死亡状态。

- 阻塞状态:

  如果一个线程执行了sleep（睡眠）、suspend（挂起）等方法，失去所占用资源之后，该线程就从运行状态进入阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就绪状态。可以分为三种：

  - 等待阻塞：运行状态中的线程执行 wait() 方法，使线程进入到等待阻塞状态。
  - 同步阻塞：线程在获取 synchronized 同步锁失败(因为同步锁被其他线程占用)。
  - 其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O 请求时，线程就会进入到阻塞状态。当sleep() 状态超时，join() 等待线程终止或超时，或者 I/O 处理完毕，线程重新转入就绪状态。

- 死亡状态:

  一个运行状态的线程完成任务或者其他终止条件发生时，该线程就切换到终止状态。

------

# 2. 线程的优先级

每一个 Java 线程都有一个优先级，这样有助于操作系统确定线程的调度顺序。

Java 线程的优先级是一个整数，其取值范围是 1 （Thread.MIN_PRIORITY ） - 10 （Thread.MAX_PRIORITY ）。

默认情况下，每一个线程都会分配一个优先级 NORM_PRIORITY（5）。

具有较高优先级的线程对程序更重要，并且应该在低优先级的线程之前分配处理器资源。但是，线程优先级不能保证线程执行的顺序，而且非常依赖于平台。

------

# 3. 创建一个线程

Java 提供了三种创建线程的方法：

- 通过实现 Runnable 接口；
- 通过继承 Thread 类本身；
- 通过 Callable 和 Future 创建线程。

------

## 通过实现 Runnable 接口来创建线程

创建一个线程，最简单的方法是创建一个实现 Runnable 接口的类。

为了实现 Runnable，一个类只需要执行一个方法调用 run()，声明如下：



public void run()

你可以重写该方法，重要的是理解的 run() 可以调用其他方法，使用其他类，并声明变量，就像主线程一样。

在创建一个实现 Runnable 接口的类之后，你可以在类中实例化一个线程对象。

Thread 定义了几个构造方法，下面的这个是我们经常使用的：

Thread(Runnable threadOb,String threadName);

这里，threadOb 是一个实现 Runnable 接口的类的实例，并且 threadName 指定新线程的名字。

新线程创建之后，你调用它的 start() 方法它才会运行。

void start();

下面是一个创建线程并开始让它执行的实例：

### 实例

```java
class RunnableDemo implements Runnable {    
    private Thread t;    
    private String threadName;        
    RunnableDemo( String name) {       
        threadName = name;       
        System.out.println("Creating " +  threadName );    
    }        
    public void run() {       
    System.out.println("Running " +  threadName );       
    try {          
        for(int i = 4; i > 0; i--) {             
            System.out.println("Thread: " + threadName + ", " + i);// 让线程睡眠一会    
            Thread.sleep(50);          
        }       
    }catch (InterruptedException e) {          
    		System.out.println("Thread " +  threadName + " interrupted.");       
    }       
    		System.out.println("Thread " +  threadName + " exiting.");    
    }        
    public void start () {       
    		System.out.println("Starting " +  threadName );       
        if (t == null) {          
            t = new Thread (this, threadName);          
            t.start ();       
        		}    
    		} 
		}   
    public class TestThread {      
    		public static void main(String args[]) {       
    		RunnableDemo R1 = new RunnableDemo( "Thread-1");       
    		R1.start();              
    		RunnableDemo R2 = new RunnableDemo( "Thread-2");       
   			R2.start();    
      	}    
}
```



编译以上程序运行结果如下：

```
Creating Thread-1
Starting Thread-1
Creating Thread-2
Starting Thread-2
Running Thread-1
Thread: Thread-1, 4
Running Thread-2
Thread: Thread-2, 4
Thread: Thread-1, 3
Thread: Thread-2, 3
Thread: Thread-1, 2
Thread: Thread-2, 2
Thread: Thread-1, 1
Thread: Thread-2, 1
Thread Thread-1 exiting.
Thread Thread-2 exiting.
```

------

## 通过继承Thread来创建线程

创建一个线程的第二种方法是创建一个新的类，该类继承 Thread 类，然后创建一个该类的实例。

继承类必须重写 run() 方法，该方法是新线程的入口点。它也必须调用 start() 方法才能执行。

该方法尽管被列为一种多线程实现方式，但是本质上也是实现了 Runnable 接口的一个实例。

### 实例

```java
class ThreadDemo extends Thread {    
  private Thread t;    
  private String threadName;        
  ThreadDemo( String name) {       
    threadName = name;       
  	System.out.println("Creating " +  threadName );    
  }       
  
  public void run() {       
  	System.out.println("Running " +  threadName );       
  try {         
  for(int i = 4; i > 0; i--) {             
  	System.out.println("Thread: " + threadName + ", " + i);             // 让线程睡眠一会
  	Thread.sleep(50);          
  	}      
  }catch (InterruptedException e) {          
    System.out.println("Thread " +  threadName + " interrupted.");       }       
    System.out.println("Thread " +  threadName + " exiting.");    }        
  public void start () {       
    System.out.println("Starting " +  threadName );       
    if (t == null) {          
      t = new Thread (this, threadName);          
      t.start ();       
    }    
  } 
}   
public class TestThread {      
  public static void main(String args[]) {       
 		ThreadDemo T1 = new ThreadDemo( "Thread-1");       
  	T1.start();             
  	ThreadDemo T2 = new ThreadDemo( "Thread-2");       
  	T2.start();    
  }    
}
```



编译以上程序运行结果如下：

```
Creating Thread-1
Starting Thread-1
Creating Thread-2
Starting Thread-2
Running Thread-1
Thread: Thread-1, 4
Running Thread-2
Thread: Thread-2, 4
Thread: Thread-1, 3
Thread: Thread-2, 3
Thread: Thread-1, 2
Thread: Thread-2, 2
Thread: Thread-1, 1
Thread: Thread-2, 1
Thread Thread-1 exiting.
Thread Thread-2 exiting.
```

------

## Thread 方法

下表列出了Thread类的一些重要方法：

| **序号** |                         **方法描述**                         |
| :------- | :----------------------------------------------------------: |
| 1        | **public void start()** 使该线程开始执行；**Java** 虚拟机调用该线程的 run 方法。 |
| 2        | **public void run()** 如果该线程是使用独立的 Runnable 运行对象构造的，则调用该 Runnable 对象的 run 方法；否则，该方法不执行任何操作并返回。 |
| 3        | **public final void setName(String name)** 改变线程名称，使之与参数 name 相同。 |
| 4        | **public final void setPriority(int priority)**  更改线程的优先级。 |
| 5        | **public final void setDaemon(boolean on)** 将该线程标记为守护线程或用户线程。 |
| 6        | **public final void join(long millisec)** 等待该线程终止的时间最长为 millis 毫秒。 |
| 7        |            **public void interrupt()** 中断线程。            |
| 8        | **public final boolean isAlive()** 测试线程是否处于活动状态。 |

测试线程是否处于活动状态。 上述方法是被Thread对象调用的。下面的方法是Thread类的静态方法。

| **序号** |                         **方法描述**                         |
| :------- | :----------------------------------------------------------: |
| 1        | **public static void yield()** 暂停当前正在执行的线程对象，并执行其他线程。 |
| 2        | **public static void sleep(long millisec)** 在指定的毫秒数内让当前正在执行的线程休眠（暂停执行），此操作受到系统计时器和调度程序精度和准确性的影响。 |
| 3        | **public static boolean holdsLock(Object x)** 当且仅当当前线程在指定的对象上保持监视器锁时，才返回 true。 |
| 4        | **public static Thread currentThread()** 返回对当前正在执行的线程对象的引用。 |
| 5        | **public static void dumpStack()** 将当前线程的堆栈跟踪打印至标准错误流。 |

### 实例

如下的ThreadClassDemo 程序演示了Thread类的一些方法：

### DisplayMessage.java 文件代码：

```
// 文件名 : DisplayMessage.java // 通过实现 Runnable 接口创建线程 public class DisplayMessage implements Runnable {    private String message;        public DisplayMessage(String message) {       this.message = message;    }        public void run() {       while(true) {          System.out.println(message);       }    } }
```



### GuessANumber.java 文件代码：

```
// 文件名 : GuessANumber.java // 通过继承 Thread 类创建线程   public class GuessANumber extends Thread {    private int number;    public GuessANumber(int number) {       this.number = number;    }        public void run() {       int counter = 0;       int guess = 0;       do {          guess = (int) (Math.random() * 100 + 1);          System.out.println(this.getName() + " guesses " + guess);          counter++;       } while(guess != number);       System.out.println("** Correct!" + this.getName() + "in" + counter + "guesses.**");    } }


```



### ThreadClassDemo.java 文件代码：

```
// 文件名 : ThreadClassDemo.java public class ThreadClassDemo {      public static void main(String [] args) {       Runnable hello = new DisplayMessage("Hello");       Thread thread1 = new Thread(hello);       thread1.setDaemon(true);       thread1.setName("hello");       System.out.println("Starting hello thread...");       thread1.start();              Runnable bye = new DisplayMessage("Goodbye");       Thread thread2 = new Thread(bye);       thread2.setPriority(Thread.MIN_PRIORITY);       thread2.setDaemon(true);       System.out.println("Starting goodbye thread...");       thread2.start();         System.out.println("Starting thread3...");       Thread thread3 = new GuessANumber(27);       thread3.start();       try {          thread3.join();       }catch(InterruptedException e) {          System.out.println("Thread interrupted.");       }       System.out.println("Starting thread4...");       Thread thread4 = new GuessANumber(75);              thread4.start();       System.out.println("main() is ending...");    } }
```



运行结果如下，每一次运行的结果都不一样。

```
Starting hello thread...
Starting goodbye thread...
Hello
Hello
Hello
Hello
Hello
Hello
Goodbye
Goodbye
Goodbye
Goodbye
Goodbye
.......
```

------

### 通过 Callable 和 Future 创建线程

- \1. 创建 Callable 接口的实现类，并实现 call() 方法，该 call() 方法将作为线程执行体，并且有返回值。
- \2. 创建 Callable 实现类的实例，使用 FutureTask 类来包装 Callable 对象，该 FutureTask 对象封装了该 Callable 对象的 call() 方法的返回值。
- \3. 使用 FutureTask 对象作为 Thread 对象的 target 创建并启动新线程。
- \4. 调用 FutureTask 对象的 get() 方法来获得子线程执行结束后的返回值。

### 实例

```java
public class CallableThreadTest implements Callable<Integer> {     
	public static void main(String[] args)       {           
	CallableThreadTest ctt = new CallableThreadTest();           
	FutureTask<Integer> ft = new FutureTask<>(ctt);           
  for(int i = 0;i < 100;i++){           				
  	System.out.println(Thread.currentThread().getName()+" 的循环变量i的值"+i);               
  	if(i==20)               {                   
  	new Thread(ft,"有返回值的线程").start();}
  }           
  try{
  System.out.println("子线程的返回值："+ft.get());
  } 
  catch (InterruptedException e){ 
    e.printStackTrace();
  } catch (ExecutionException e){ 
  	e.printStackTrace();}
  }    
  @Override       
  public Integer call() throws Exception{ int i = 0;
  for(;i<100;i++){
  	System.out.println(Thread.currentThread().getName()+" "+i);           
  }           
  return i;
  }
}
```



------

## 创建线程的三种方式的对比

- \1. 采用实现 Runnable、Callable 接口的方式创建多线程时，线程类只是实现了 Runnable 接口或 Callable 接口，还可以继承其他类。
- \2. 使用继承 Thread 类的方式创建多线程时，编写简单，如果需要访问当前线程，则无需使用 Thread.currentThread() 方法，直接使用 this 即可获得当前线程。

------

# 4. 线程的几个主要概念

在多线程编程时，你需要了解以下几个概念：

- 线程同步
- 线程间通信
- 线程死锁
- 线程控制：挂起、停止和恢复

------

# 5. 多线程的使用

有效利用多线程的关键是理解程序是并发执行而不是串行执行的。例如：程序中有两个子系统需要并发执行，这时候就需要利用多线程编程。

通过对多线程的使用，可以编写出非常高效的程序。不过请注意，如果你创建太多的线程，程序执行的效率实际上是降低了，而不是提升了。

请记住，上下文的切换开销也很重要，如果你创建了太多的线程，CPU 花费在上下文的切换的时间将多于执行程序的时间！

# 6. JAVA多线程，真的提高了效率吗？



在面试的时候被问了一个多线程的问题
 回来仔细思考了一下，多线程是否真的能提高了效率？
 我对多线程的理解就是：
 比如挖一个隧道，有2种开工方法
 1、只在山的一头挖，直至挖到山的另一头，从而打通隧道，这可以看成是单线程

 2、在山的两头挖，同时开工，最后在山的中间接通，从而打通隧道，这感觉肯定比1快了很多，好比多线程

 但是2成立的前提是必须有两个工人。而我们的计算机中一般来说只有一个CPU，也就是说只有一个工人。
 多线程不过是CPU在不同的时间片之间切换，而表现出齐头并进的样子。

 既然挖隧道的人只有一个，虽然我的施工方案是在山的两头开挖，但是由于工作的人只有一个，所以只有让这个人在山的两头跑，挖一会这头再去挖另一头，来回跑是要花费额外时间的（好比线程的切换和调度）。

 那么，我们是不是可以说，在单CPU的机器中，多线程反而降低了效率呢？

 1.
 不能一概而论，你的看多线程在你的程序中为啥而生。在单cpu系统，比如有io的等待，多线程也能提高效率
 2
 楼主提的问题很有意思。经典的解释是 －如果cpu确实是一个挖山工人，那么它工作就好像是挖1个小时，然后休息10个小时；这期间如果让它跑到山那头继续挖，效率还是很高的。

 现在问题是 －它是否工作1小时然后休息10小时？答案是肯定的。现在的程序时间大多花在读取数据上，真正的计算工作花时间还是相对少的，因此cpu很大时间表现都很闲，就像挖山，挖土效率高，运土效率低。多线程就是要充分利用它的挖土效率
 3
 pc机不光只一个cpu，cpu和其它硬件设备一起才能完成计算，分工协作，但可能出现其中某个家伙偷懒或效率低，导致大家都等它，闲着的其它设备这个时候可以腾出手来干其它活。单cpu在同一时刻只能干一件事情，这没有问题，问题是它并不是7*24*3600都在干活，其它设备也是同样的道理，多线程的目的可以最大限度的提高硬件设备的利用率。
 4
 同一个设备可以同时干几件事情，但一个设备在同一时刻肯定只能干一件事情，一般我们说并行或串行，都在以时间段来看的而不是以时刻来看的，比如你一边上je消遣还一边写代码干活，在一定的时间范围内，你是并行的，但如果这个时间范围你划分得非常非常短，那么你是串行的

 5
 一个cpu可以多线程。但是一个单核的cpu任何时间点，都只能在做一个任务。
 如果只是像楼主说的挖隧道这么简单的事，那么的确多线程没用。
 只不过很可惜，计算机不像拿铁锹挖隧道这么简单。

 6
 假设每挖5分钟，就需要清理一下挖出来的石土。有一个小车在清理它们。
 工人只有一个。
 单线程的做法是： 挖5分钟。然后工人停止挖，小车清理石土的5分钟里，工人在等待。
 2个线程的做发是： 挖5分钟，小车来清理石土。这5分钟里，工人在另一头挖。

 也不是很恰当的比喻。不过至少能说明点问题。
 小车清理石土，就相当于磁盘io等相对于cpu计算来说比较慢的操作。

 cpu不会等着io的完成，而去执行另一个进程的计算任务。
 这边io完成时好象是会发出什么信号来着，忘了。计算机原理都还给老师了，惭愧啊。
 7

 如楼主所举的例子,我来解惑。

 如果一个机器人代表CUP，哪么这个机器人一天所做的事情，并不都是只挖山。

 它还有许多事情要做，比如砍柴，烧水，钓鱼，挖山等等等。

 如果按以上划分是 4条线程， 每一个线程大概占用1/4CUP时间。

 如果你的设定 在挖山这一快 多设几次同一个任务。 比如设定到 挖山共有3条线程。

 哪么 挖山的CUP占用率将达到 1/2 这就是所谓的提高了效率。

 现实中的CPU 在大部分时候的 闲置状态的。
 因此 开多条线程能提高效率 不如说成是 充分利用了CPU执行时间。

 8
 楼主举的例子是并行，在资源有剩余的情况下（比如人都堆到一个洞里干不开），肯定是提高效率。如果资源有冲突（人手只够从一个方向挖，比如只一个CPU），那就是并发了，不一定能提高效率。

 我想了个例子：


  假设人手只够从一个方向挖洞。
    挖洞时，总得把洞里的土运出去吧。洞越深，运土越占用时间，如果一大伙人都在那挖洞，等挖出一车土，然后一起坐着车运土（带装卸），那路上那些人就闲着了（挖土时司机也会闲着）。为了提高工作效率，那就把人分成三组，一组人（一个挖土线程）挖土，两组人运土（两辆车，两个运土线程）。

 9

 我认为啊，单CPU单核、纯计算、没IO的理想状态下，单个线程肯定比多个线程快，因为省去了线程切换的开销。但真实的环境基本都有IO操作，在异步的业务场景下，我一般会使用线程池，至于线程池的线程数目配置为多少，有资料推荐为N×（1+IO耗时/完整的业务耗时），N是CPU核数。

 10
 最简单的如web server，如果单线程的话，一个server同时只能接受一个用户的点击。
 还点击率呢，直接就绿了。
 另外多线程和快不快没有直接关系。最主要的是可以并发执行。
 纯粹比较同一个任务在单线程还是多线程模式下快的话，肯定是单线程快。因为多线程会有一个线程调度的消耗。但是最为一个系统，多线程的优势是非常明显的。如果Java没有多线程直接可以去死了。
 当年红极一时的plam系统因为对多线程支持的不好，在网络和媒体应用方面败下阵来。

 11

 多线程效率 我认为未必会高，而且有时候相反会低。
 多线程并不是为了提高效率，而是不必等待 可以并行执行多条数据。
 可以这么想 我们通过xp系统复制文件。你可以复制一份文件这叫是单线呈，但是你要等这个复制完了才能复制另一份文件，而且不能多复制。这样很难受，所以你可以选择多复制文件,这就是多线程。但复制多份文件用的时间未必会比一份一份文件所用时间少。只是它合理利用了时间进行了多个操作。
     如果是买票系统就会用到多线呈。买票是同时进行的，如果一个用户一个用户等下去不是办法，所以可以多个用户同时买票，效率也就提高了。这里的效率不是执行的效率而是时间的合理利用,多个线呈同时进行。

 12
 单线程,多线程,线程池,都是不同问题的不同解决策略,不存在谁的效率一定高的问题.

 一个时间服务器,一个线程处理请求就可以了
 FTP,HTTP服务器,就不一样了,请求多,处理响应时间长,必须得有多个线程来处理,
 线程池是多线程的一种改良方式
 当然以上指的都是BIO的情况.
 在NIO下,处理请求用单线程就可以了,因为它不存在IO阻塞的问题

 13
 楼主的例子举的还算生动，但思路有点问题。在大多数场景中，各个线程不应该是同时去做同一件事情，而是各谋其职，协调工作，从而最大限度的利用系统资源。而系统资源并不仅仅是CPU，还有I/O或带宽等等。

 就楼主的例子而言，可以想象成两个线程，A线程的任务是挖，B线程的任务是把挖开的土石运走，从而提高效率，这也就是经典的生产者消费者模式。

 14
 生产者-消费者模型，如果你是用多线程实现了的，那完全也可以写成单线程的（当然，单线程也就是一个顺序执行，恐怕不能称为“生产-消费”了）。
    之所以设计成生产者-消费者的模式，是因为生产者和消费者不能步调一致吧？！因为会出现等待的情况，所以要按“生产者-消费者”的方式，用多线程实现（比如3个生产者线程，2个消费者线程）。这充分利用了系统资源，如果效率还没有提高，那真不知道要干啥呢——比如说，生产者干的事就是a+1，消费者干的事就是a-1，那何必费劲做成“生产者-消费者”呢（专门做出一个生产者线程对一个消费者线程，也太傻了吧）？

    上面已经有人说了，系统运行环境下的资源并不只有CPU，还有网络，数据库（可能安装在另一个机器上）。数据库访问和网络的IO操作都是比较耗时的，这时候CPU会闲一些。使用多线程可以调配资源的使用率。
    
    PS：假设你的程序部署到一个配置特牛的服务器上，感觉还是不足以应付业务量，结果一查CPU占用率，才3%，你的程序是不是写的很失败？

 15
 我觉得lz举的例子不太合适,一个CPU它不是一个工人,按WINDOWS的比喻,一个CPU应该是100个工人.
 100个工人挖山从一头挖,最多同时能20个人一起挖,其他80个人休息.(这是单线程)
 如果两头挖,最多同时40人一起挖,60个人休息.(这是多线程)
 所以多线程只能提高CPU的使用效率.
 一头挖山只使用CPU的20%,两头挖山可能就会使用CPU的50%,因为启动一条新的线程也会有CUP开销.
 如果在工人足够多的时候,用多多线程,是可以提前完工的.
 如果在工人不足的时候,只能用单线程.
 声明下一个CPU它不是一个人!!!





# 7. 线程池的原理及实现

**1、线程池简介：**
    多线程技术主要解决处理器单元内多个线程执行的问题，它可以显著减少处理器单元的闲置时间，增加处理器单元的吞吐能力。   
    假设一个服务器完成一项任务所需时间为：T1 创建线程时间，T2 在线程中执行任务的时间，T3 销毁线程时间。

​    如果：T1 + T3 远大于 T2，则可以采用线程池，以提高服务器性能。
​                一个线程池包括以下四个基本组成部分：
​                1、线程池管理器（ThreadPool）：用于创建并管理线程池，包括 创建线程池，销毁线程池，添加新任务；
​                2、工作线程（PoolWorker）：线程池中线程，在没有任务时处于等待状态，可以循环的执行任务；
​                3、任务接口（Task）：每个任务必须实现的接口，以供工作线程调度任务的执行，它主要规定了任务的入口，任务执行完后的收尾工作，任务的执行状态等；
​                4、任务队列（taskQueue）：用于存放没有处理的任务。提供一种缓冲机制。
​               
​    线程池技术正是关注如何缩短或调整T1,T3时间的技术，从而提高服务器程序性能的。它把T1，T3分别安排在服务器程序的启动和结束的时间段或者一些空闲的时间段，这样在服务器程序处理客户请求时，不会有T1，T3的开销了。
​    线程池不仅调整T1,T3产生的时间段，而且它还显著减少了创建线程的数目，看一个例子：
​    假设一个服务器一天要处理50000个请求，并且每个请求需要一个单独的线程完成。在线程池中，线程数一般是固定的，所以产生线程总数不会超过线程池中线程的数目，而如果服务器不利用线程池来处理这些请求则线程总数为50000。一般线程池大小是远小于50000。所以利用线程池的服务器程序不会为了创建50000而在处理请求时浪费时间，从而提高效率。

​    代码实现中并没有实现任务接口，而是把Runnable对象加入到线程池管理器（ThreadPool），然后剩下的事情就由线程池管理器（ThreadPool）来完成了

 



 

测试代码：

**[java]** [copy](http://blog.csdn.net/touch_2011/article/details/6914468#)



1. **package** mine.util.thread;  
2.   
3. //测试线程池  
4. **public** **class** TestThreadPool {  
5. ​    **public** **static** **void** main(String[] args) {  
6. ​        // 创建3个线程的线程池  
7. ​        ThreadPool t = ThreadPool.getThreadPool(3);  
8. ​        t.execute(**new** Runnable[] { **new** Task(), **new** Task(), **new** Task() });  
9. ​        t.execute(**new** Runnable[] { **new** Task(), **new** Task(), **new** Task() });  
10. ​        System.out.println(t);  
11. ​        t.destroy();// 所有线程都执行完成才destory  
12. ​        System.out.println(t);  
13. ​    }  
14.   
15. ​    // 任务类  
16. ​    **static** **class** Task **implements** Runnable {  
17. ​        **private** **static** **volatile** **int** i = 1;  
18.   
19. ​        @Override  
20. ​        **public** **void** run() {// 执行任务  
21. ​            System.out.println("任务 " + (i++) + " 完成");  
22. ​        }  
23. ​    }  
24. }  


 

运行结果：

WorkThread number:3  finished task number:0  wait task number:6
任务 1 完成
任务 2 完成
任务 3 完成
任务 4 完成
任务 5 完成
任务 6 完成
WorkThread number:3  finished task number:6  wait task number:0

分析：由于并没有任务接口，传入的可以是自定义的任何任务，所以线程池并不能准确的判断该任务是否真正的已经完成（真正完成该任务是这个任务的run方法执行完毕），只能知道该任务已经出了任务队列，正在执行或者已经完成。



**2、java类库中提供的线程池简介：**

​     **java提供的线程池更加强大，相信理解线程池的工作原理，看类库中的线程池就不会感到陌生了。**

![img](http://hi.csdn.net/attachment/201110/28/0_1319784225fRSR.gif)

![img](http://hi.csdn.net/attachment/201110/28/0_1319784243mu5f.gif)

 

