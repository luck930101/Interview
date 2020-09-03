**前言**

对象的内存分配，往大的方向上讲，就是在堆上分配，少数情况下也可能会直接分配在老年代中，分配的规则并不是百分之百固定的，其细节决定于当前使用的是哪种垃圾收集器组合，当然还有虚拟机中与内存相关的参数。垃圾收集器组合一般就是Serial+Serial Old和Parallel+Serial Old，前者是Client模式下的默认垃圾收集器组合，后者是Server模式下的默认垃圾收集器组合，文章使用对比学习法对比Client模式下和Server模式下同一条对象分配原则有什么区别。

 

**TLAB**

首先讲讲什么是TLAB。内存分配的动作，可以按照线程划分在不同的空间之中进行，即每个线程在Java堆中预先分配一小块内存，称为本地线程分配缓冲（Thread Local Allocation Buffer，TLAB）。哪个线程需要分配内存，就在哪个线程的TLAB上分配。虚拟机是否使用TLAB，可以通过-XX:+/-UseTLAB参数来设定。这么做的目的之一，也是为了并发创建一个对象时，保证创建对象的线程安全性。TLAB比较小，直接在TLAB上分配内存的方式称为快速分配方式，而TLAB大小不够，导致内存被分配在Eden区的内存分配方式称为慢速分配方式。

 

**对象优先分配在Eden区上**

上面讲了不同的垃圾收集器组合对于内存分配规则是有影响的，看下影响在什么地方并解释一下原因，虚拟机参数为“-verbose:gc -XX:+PrintGCDetails -Xms20M -Xmx20M -Xmn10M -XX:SurvivorRatio=8”，即10M新生代，10M老年代，10M新生代中8M的Eden区，两个Survivor区各1M。代码都是同一段

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class EdenAllocationTest
{
    private static final int _1MB = 1024 * 1024;
    
    public static void main(String[] args)
    {
        byte[] allocation1 = new byte[2 * _1MB];
        byte[] allocation2 = new byte[2 * _1MB];
        byte[] allocation3 = new byte[2 * _1MB];
        byte[] allocation4 = new byte[4 * _1MB];
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

Client模式下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
[GC [DefNew: 6487K->194K(9216K), 0.0042856 secs] 6487K->6338K(19456K), 0.0043281 secs] [Times: user=0.00 sys=0.00, real=0.00 secs] 
Heap
 def new generation   total 9216K, used 4454K [0x0000000005180000, 0x0000000005b80000, 0x0000000005b80000)
  eden space 8192K,  52% used [0x0000000005180000, 0x00000000055a9018, 0x0000000005980000)
  from space 1024K,  18% used [0x0000000005a80000, 0x0000000005ab0810, 0x0000000005b80000)
  to   space 1024K,   0% used [0x0000000005980000, 0x0000000005980000, 0x0000000005a80000)
 tenured generation   total 10240K, used 6144K [0x0000000005b80000, 0x0000000006580000, 0x0000000006580000)
   the space 10240K,  60% used [0x0000000005b80000, 0x0000000006180048, 0x0000000006180200, 0x0000000006580000)
 compacting perm gen  total 21248K, used 2982K [0x0000000006580000, 0x0000000007a40000, 0x000000000b980000)
   the space 21248K,  14% used [0x0000000006580000, 0x0000000006869890, 0x0000000006869a00, 0x0000000007a40000)
No shared spaces configured.
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

Server模式下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
Heap
 PSYoungGen      total 9216K, used 6651K [0x000000000af20000, 0x000000000b920000, 0x000000000b920000)
  eden space 8192K, 81% used [0x000000000af20000,0x000000000b59ef70,0x000000000b720000)
  from space 1024K, 0% used [0x000000000b820000,0x000000000b820000,0x000000000b920000)
  to   space 1024K, 0% used [0x000000000b720000,0x000000000b720000,0x000000000b820000)
 PSOldGen        total 10240K, used 4096K [0x000000000a520000, 0x000000000af20000, 0x000000000af20000)
  object space 10240K, 40% used [0x000000000a520000,0x000000000a920018,0x000000000af20000)
 PSPermGen       total 21248K, used 2972K [0x0000000005120000, 0x00000000065e0000, 0x000000000a520000)
  object space 21248K, 13% used [0x0000000005120000,0x0000000005407388,0x00000000065e0000)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

看到在**Client模式下，最后分配的4M在新生代中，先分配的6M在老年代中；在Server模式下，最后分配的4M在老年代中，先分配的6M在新生代中**。说明不同的垃圾收集器组合对于对象的分配是有影响的。讲下两者差别的原因：

1、Client模式下，新生代分配了6M，虚拟机在GC前有6487K，比6M也就是6144K多，多主要是因为TLAB和EdenAllocationTest这个对象占的空间，TLAB可以通过“-XX:+PrintTLAB”这个虚拟机参数来查看大小。OK，6M多了，然后来了一个4M的，Eden+一个Survivor总共就9M不够分配了，这时候就会触发一次Minor GC。但是触发Minor GC也没用，因为allocation1、allocation2、allocation3三个引用还存在，另一块1M的Survivor也不够放下这6M，那么这次Minor GC的效果其实是通过分配担保机制将这6M的内容转入老年代中。然后再来一个4M的，由于此时Minor GC之后新生代只剩下了194K了，够分配了，所以4M顺利进入新生代。

2、Server模式下，前面都一样，但是在GC的时候有一点区别。在GC前还会进行一次判断，如果要分配的内存>=Eden区大小的一半，那么会直接把要分配的内存放入老年代中。要分配4M，Eden区8M，刚好一半，而且老年代10M，够分配，所以4M就直接进入老年代去了。为了验证一下结论，我们把3个2M之后分配的4M改为3M看一下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class EdenAllocationTest
{
    private static final int _1MB = 1024 * 1024;
    
    public static void main(String[] args)
    {
        byte[] allocation1 = new byte[2 * _1MB];
        byte[] allocation2 = new byte[2 * _1MB];
        byte[] allocation3 = new byte[2 * _1MB];
        byte[] allocation4 = new byte[3 * _1MB];
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果为

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
[GC [PSYoungGen: 6487K->352K(9216K)] 6487K->6496K(19456K), 0.0035661 secs] [Times: user=0.00 sys=0.00, real=0.00 secs] 
[Full GC [PSYoungGen: 352K->0K(9216K)] [PSOldGen: 6144K->6338K(10240K)] 6496K->6338K(19456K) [PSPermGen: 2941K->2941K(21248K)], 0.0035258 secs] [Times: user=0.02 sys=0.00, real=0.00 secs] 
Heap
 PSYoungGen      total 9216K, used 3236K [0x000000000af40000, 0x000000000b940000, 0x000000000b940000)
  eden space 8192K, 39% used [0x000000000af40000,0x000000000b269018,0x000000000b740000)
  from space 1024K, 0% used [0x000000000b740000,0x000000000b740000,0x000000000b840000)
  to   space 1024K, 0% used [0x000000000b840000,0x000000000b840000,0x000000000b940000)
 PSOldGen        total 10240K, used 6338K [0x000000000a540000, 0x000000000af40000, 0x000000000af40000)
  object space 10240K, 61% used [0x000000000a540000,0x000000000ab70858,0x000000000af40000)
 PSPermGen       total 21248K, used 2982K [0x0000000005140000, 0x0000000006600000, 0x000000000a540000)
  object space 21248K, 14% used [0x0000000005140000,0x0000000005429890,0x0000000006600000)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

看到3M在新生代中，6M通过分配担保机制进入老年代了。

 

**大对象直接进入老年代**

虚拟机参数为“-XX:+PrintGCDetails -Xms20M -Xmx20M -Xmn10M -XX:SurvivorRatio=8 -XX:PretenureSizeThreshold=3145728”，最后那个参数表示大于这个设置值的对象直接在老年代中分配，这样做的目的是为了避免在Eden区和两个Survivor区之间发生大量的内存复制。测试代码为

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class OldTest
{
    private static final int _1MB = 1024 * 1024;
    
    public static void main(String[] args)
    {
         byte[] allocation = new byte[4 * _1MB];
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

Client模式下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
Heap
 def new generation   total 9216K, used 507K [0x0000000005140000, 0x0000000005b40000, 0x0000000005b40000)
  eden space 8192K,   6% used [0x0000000005140000, 0x00000000051bef28, 0x0000000005940000)
  from space 1024K,   0% used [0x0000000005940000, 0x0000000005940000, 0x0000000005a40000)
  to   space 1024K,   0% used [0x0000000005a40000, 0x0000000005a40000, 0x0000000005b40000)
 tenured generation   total 10240K, used 4096K [0x0000000005b40000, 0x0000000006540000, 0x0000000006540000)
   the space 10240K,  40% used [0x0000000005b40000, 0x0000000005f40018, 0x0000000005f40200, 0x0000000006540000)
 compacting perm gen  total 21248K, used 2972K [0x0000000006540000, 0x0000000007a00000, 0x000000000b940000)
   the space 21248K,  13% used [0x0000000006540000, 0x00000000068272a0, 0x0000000006827400, 0x0000000007a00000)
No shared spaces configured.
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

Server模式下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
Heap
 PSYoungGen      total 9216K, used 4603K [0x000000000afc0000, 0x000000000b9c0000, 0x000000000b9c0000)
  eden space 8192K, 56% used [0x000000000afc0000,0x000000000b43ef40,0x000000000b7c0000)
  from space 1024K, 0% used [0x000000000b8c0000,0x000000000b8c0000,0x000000000b9c0000)
  to   space 1024K, 0% used [0x000000000b7c0000,0x000000000b7c0000,0x000000000b8c0000)
 PSOldGen        total 10240K, used 0K [0x000000000a5c0000, 0x000000000afc0000, 0x000000000afc0000)
  object space 10240K, 0% used [0x000000000a5c0000,0x000000000a5c0000,0x000000000afc0000)
 PSPermGen       total 21248K, used 2972K [0x00000000051c0000, 0x0000000006680000, 0x000000000a5c0000)
  object space 21248K, 13% used [0x00000000051c0000,0x00000000054a72a0,0x0000000006680000)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

看到**Client模式下4M直接进入了老年代，Server模式下4M还在新生代中**。产生这个差别的原因是**“-XX:PretenureSizeThreshold”这个参数对Serial+Serial Old垃圾收集器组合有效而对Parallel+Serial Old垃圾收集器组合无效**。

 

**其他几条原则**

上面列举的原则其实不重要，只是演示罢了，也不需要记住，因为实际过程中我们可能使用的并不是上面的垃圾收集器的组合，可能使用ParNew垃圾收集器，可能使用G1垃圾收集器。场景很多，重要的是要在实际使用的时候有办法知道使用的垃圾收集器对于对象分配有哪些原则，因为理解这些原则才是调优的第一步。下面列举一下对象分配的另外两条原则：

1、长期存活的对象将进入老年代。Eden区中的对象在一次Minor GC后没有被回收，则对象年龄+1，当对象年龄达到“-XX:MaxTenuringThreshold”设置的值的时候，对象就会被晋升到老年代中

2、Survivor空间中相同年龄的所有对象大小总和大于Survivor空间的一半，年龄大于或等于该年龄的对象就可以直接进入老年代，无须等到“-XX:MaxTenuringThreshold”设置要求的年龄

