**之后写的东西就会用到虚拟机参数了，现在这里汇个总自己平时用到的、看到的一些虚拟机参数。现在看不懂没关系，反正之后都会用到的：**

（1）-Xms20M

表示设置JVM启动内存的最小值为20M，必须以M为单位

（2）-Xmx20M

表示设置JVM启动内存的最大值为20M，必须以M为单位。将-Xmx和-Xms设置为一样可以避免JVM内存自动扩展。大的项目-Xmx和-Xms一般都要设置到10G、20G甚至还要高

（3）-verbose:gc

表示输出虚拟机中GC的详细情况

（4）-Xss128k

表示可以设置虚拟机栈的大小为128k

（5）-Xoss128k

表示设置本地方法栈的大小为128k。不过HotSpot并不区分虚拟机栈和本地方法栈，因此对于HotSpot来说这个参数是无效的

（6）-XX:PermSize=10M

表示JVM初始分配的永久代的容量，必须以M为单位

（7）-XX:MaxPermSize=10M

表示JVM允许分配的永久代的最大容量，必须以M为单位，大部分情况下这个参数默认为64M

（8）-Xnoclassgc

表示关闭JVM对类的垃圾回收

（9）-XX:+TraceClassLoading

表示查看类的加载信息

（10）-XX:+TraceClassUnLoading

表示查看类的卸载信息

（11）-XX:NewRatio=4

表示设置年轻代：老年代的大小比值为1：4，这意味着年轻代占整个堆的1/5

（12）-XX:SurvivorRatio=8

表示设置2个Survivor区：1个Eden区的大小比值为2:8，这意味着Survivor区占整个年轻代的1/5，这个参数默认为8

（13）-Xmn20M

表示设置年轻代的大小为20M

（14）-XX:+HeapDumpOnOutOfMemoryError

表示可以让虚拟机在出现内存溢出异常时Dump出当前的堆内存转储快照

（15）-XX:+UseG1GC

表示让JVM使用G1垃圾收集器

（16）-XX:+PrintGCDetails

表示在控制台上打印出GC具体细节

（17）-XX:+PrintGC

表示在控制台上打印出GC信息

（18）-XX:PretenureSizeThreshold=3145728

表示对象大于3145728（3M）时直接进入老年代分配，这里只能以字节作为单位

（19）-XX:MaxTenuringThreshold=1

表示对象年龄大于1，自动进入老年代

（20）-XX:CompileThreshold=1000

表示一个方法被调用1000次之后，会被认为是热点代码，并触发即时编译

（21）-XX:+PrintHeapAtGC

表示可以看到每次GC前后堆内存布局

（22）-XX:+PrintTLAB

表示可以看到TLAB的使用情况

（23）-XX:+UseSpining

开启自旋锁

（24）-XX:PreBlockSpin

更改自旋锁的自旋次数，使用这个参数必须先开启自旋锁

 

**怎么用MyEclipse设置虚拟机参数**

右键类-->Run as-->Run Configurations...

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150922215854365-1645287112.png)

Java Application里面选到自己的类，选择Arguments，VM arguments空白部分就可以设置虚拟机参数了。如果点击了Run Configurations没有出现自己的类的话也没关系，双击一下Java Application就好了

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150922220053569-1129454509.png)

 

**后记**

Java虚拟机参数有上百个，性能调优中很大一块就是选择这上百个参数中的某些重要参数进行设置，并且根据项目运行情况对参数进行不断调整以求达到一个性能最佳点。性能调优说有捷径也有捷径，百度搜一份别人推荐的JVM参数设置改改就好了，那至于具体好不好就说不上了，但起码保证能用吧；性能调优说没捷径也没捷径，如果对JVM的性能有严苛的要求并且希望细化到每一个小点，达到能达到的最佳值，那首先就必须对于Java虚拟机，对于每一个虚拟机参数有着深刻的理解才行。最近几年兴起了一个叫做性能调优师的职位，也证明了性能优化的重要性，反正从个人的角度看，性能调优绝对是一门学问，不是那么简单的，打好基础才是王道。