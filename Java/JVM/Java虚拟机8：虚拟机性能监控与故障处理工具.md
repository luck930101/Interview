**前言**

定位系统问题的时候，知识、经验是基础，数据是依据，工具是运用知识处理数据的手段。这里说的数据包括：运行日志、异常堆栈、GC日志、线程快照、堆转储快照等。经常使用适当的虚拟机监控和分析的工具可以加快分析数据、定位解决问题的速度。

 

**jps：虚拟机进程状况工具**

首先约定一下运行的代码都是以下这段

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 public class TestMain
 2 {
 3     public static void main(String[] args)
 4     {
 5         while (true)
 6         {
 7             
 8         }
 9     }
10 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

JDK的很多小工具的名字都参考了UNIX命令的命名方式，jps（JVM Process Status）是其中的典型。除了名字像UNIX的ps命令外，它的功能也和ps命令类似：可以列出正在运行的虚拟机进程，并显示虚拟机执行主类名称以及这些进程的本地虚拟机唯一ID（Local Virtual Machine Identifier,LVMID）。虽然功能比较单一，但它是使用最高的JDK命令行工具，因为其他的JDK工具大多需要输入它查询到的LVMID来确定要监控的是哪一个虚拟机进程。

**jps命令格式：**

jps [ options ] [ hostid ]

**jps工具主要选项**

| **选    项** | **作            用**                                 |
| ------------ | ---------------------------------------------------- |
| -q           | 只输出LVMID，省略主类的名称                          |
| -m           | 输出虚拟机进程启动时传递给主类main()函数的参数       |
| -l           | 输出主类的全名，如果进程执行的是jar包，输出jar包路径 |
| -v           | 输出虚拟机进程启动时的JVM参数                        |

**jps执行样例**

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150927172759756-1369001787.png)

某个虚拟机进程执行TestMain这个类的main方法，看到10492就是该虚拟机进程的ID

 

**jstat：虚拟机统计信息监控工具**

jstat（JVM Statistics Monitoring Tool）使用于监视虚拟机各种运行状态信息的命令行工具。它可以显示本地或者远程（需要远程主机提供RMI支持）虚拟机进程中的类信息、内存、垃圾收集、JIT编译等运行数据，在没有GUI，只提供了纯文本控制台环境的服务器上，它将是运行期间定位虚拟机性能问题的首选工具。

**jstat命令格式**

jstat [ option vmid [ interval [ s | ms ] [ count ] ] ]

这个VMID，对于本地虚拟机进程而言，VMID和LVMID是一致的。参数interval和count分别表示查询间隔和次数，如果省略这两个参数，说明只查询一次，假设需要每250毫秒查询一次进程2764的垃圾收集情况，一共查询20次，那命令应当是：

**jstat -gc 2764 250 20**

**jstat主要工具选项**

| **选       项**   | **作              用**                                       |
| ----------------- | ------------------------------------------------------------ |
| -class            | 监视类装载、卸载数量、总空间以及类装载所耗费的时间           |
| -gc               | 监视Java堆状况，包括Eden区、两个Survivor区、、老年代、永久带等的容量、已用空间、GC时间合计等信息 |
| -gccapacity       | 监视内容基本与-gc相同，但输出主要关注Java堆各个区域使用到的最大、最小空间 |
| -gcutil           | 监视内容基本与-gc相同，但输出主要关注已使用的空间占总空间的百分比 |
| -gccause          | 与-gcutil功能一样，但是会额外输出导致上一次GC产生的原因      |
| -gcnew            | 监视新生代GC状况                                             |
| -gcnewcapacity    | 监视内容基本与-gcnew相同，但输出主要关注使用到的最大、最小空间 |
| -gcold            | 监视老年代GC状况                                             |
| -gcoldcapacity    | 监视内容基本与-gcold相同，但输出主要关注使用到的最大、最小空间 |
| -gcpermcapacity   | 输出永久代使用到的最大、最小空间                             |
| -compiler         | 输出JIT编译器编译过的方法、耗时等信息                        |
| -printcompilation | 输出已经被JIT编译的方法                                      |

**jstat执行样例**

jstat监视选项众多，举一个例子来查看一下该命令如何查看监视结果

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150927175643069-377631724.png)

查询结果表明，新生代Eden区（E，表示Eden）使用了2%的空间，两个Survivor区（S0、S1，表示Survivor0、Survivor1）都是空的，老年代（O，表示Old）和永久带（P。表示Permanent）则分别使用了0%和13.84%的空间。程序运行以来共发生Minor GC（YGC，表示Young GC）0次，总共耗时0秒；发生Full GC（FGC，表示Full GC）3次，Full GC共耗时（FGCT，Full GC Time）为0秒，所有GC总耗时（GCT，表示GC Time）0秒。

 

**jinfo：Java配置信息工具**

jinfo（Configuration Info for Java）的作用是实时地查看和调整虚拟机各项参数。使用jps命令的-v可以查看虚拟机启动时显式指定的参数列表，但如果想知道未被显式指定的参数的系统默认值，可以使用jinfo的-flag选项进行查询，jinfo还可以使用-sysprops选项把虚拟机进程的System.getProperties()的内容打印出来。

**jinfo命令格式**

jinfo [ option ] pid

**jinfo执行样例**

jinfo这个命令对于Windows平台有较大限制，在Linux和Solaris系统才可以正常使用，所以这里就不演示了。

 

**jmap：Java内存映像工具**

jmap（Memory Map for Java）命令用于生成堆转储快照。如果不使用jmap命令，要想获取Java堆转储，可以使用“-XX:+HeapDumpOnOutOfMemoryError”参数，可以让虚拟机在OOM异常出现之后自动生成dump文件，Linux命令下可以通过kill -3发送进程退出信号也能拿到dump文件。

jmap的作用并不仅仅是为了获取dump文件，它还可以查询finalize执行队列、Java堆和永久代的详细信息，如空间使用率、当前使用的是哪种收集器等。和jinfo一样，jmap有不少功能在Windows平台下也是受限制的，除了生成dump文件的-dump选项和用于查看每个类的实例、空间占用统计的-histo选项在所有操作系统都提供之外，其余选项都只能在Linux和Solaris系统下使用。

**jmap命令格式**

jmap [ option ] vmid

**jmap工具主要选项**

| **选             项** | **作          用**                                           |
| --------------------- | ------------------------------------------------------------ |
| -dump                 | 生成Java堆转储快照。格式为-dump:[live, ]format=b,file=<filename>，其中live自参数说明是否只dump出存活的对象 |
| -finalizerinfo        | 显示在F-Queue中等待Finalizer线程执行finalize方法的对象。只在Linux和Solaris系统下有效 |
| -heap                 | 显示Java堆详细信息，如使用哪种收集器、参数配置、分代状况等。只在Linux和Solaris系统下有效 |
| -histo                | 显示堆中对象统计信息，包括类、实例数量、合计容量             |
| -permstat             | 以ClassLoader为统计口径显示永久代内存状态。只在Linux和Solaris系统下有效 |
| -F                    | 当虚拟机进行对-dump选项没有响应时，可使用这个选项强制生成dump快照。只在Linux和Solaris系统下有效 |

**jmap执行样例**

同样，这个命令对Window环境限制也比较大，就不演示了。

 

**jstack：Java堆栈跟踪工具**

jstack（Stack Trace for Java）命令用于生成虚拟机当前时刻的线程快照。线程快照就是当前虚拟机内每一条线程正在执行的方法堆栈的集合，生成线程快照的目的主要是定位线程长时间出现停顿的原因，如线程间死锁、死循环、请求外部资源导致的长时间等待等都是导致线程长时间停顿的原因。线程出现停顿的时候通过jstack来查看各个线程的调用堆栈，就可以知道没有响应的线程到底在后台做些什么事情，或者在等待些什么资源。

**jstack命令格式**

jstack [ option ] vmid

**jstack主要工具选项**

| **选    项** | **作             用**                         |
| ------------ | --------------------------------------------- |
| -F           | 当正常输出的请求不被响应时，强制输出线程堆栈  |
| -l           | 除堆栈外，显示关于锁的附加信息                |
| -m           | 如果调用到本地方法的时候，可以显示C/C++的堆栈 |

**jstack执行样例**

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150927184442600-2117979198.png)

只截取一部分，看到这就是10492这个虚拟机进程ID当前时刻的线程快照。线程处于RUNNABLE状态，执行到了TestMain函数的第7行，并且一直停留在第7行。

 

**其他**

上面都是利用命令采集指定进程的虚拟机运行时的信息，实际上，还可以利用可视化工具对指定PID的虚拟机运行时信息进行监控，这里推荐两个：

1、JConsole

在Java_HOME/bin目录下，有一个jconsole.exe，双击运行一下就可以了。

2、Visual VM

这个是到目前为止随JDK发布的功能最为强大的运行监视和故障处理工具，除了最基本的运行监视、 故障处理外，还有性能分析的功能，且十分强大。Visual VM还有一个很大的优点，它对应用程序的实际性能影响很小，使得它可以直接应用在生产环境中。

至于具体如何使用，就不演示了，比较简单。除了上面两个工具，还可以使用JProfiler、YourKit等专业且收费的Profiling工具。