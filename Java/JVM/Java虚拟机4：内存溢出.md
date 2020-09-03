**堆溢出**

堆内存里面存放new创建的对象和数组。Java堆唯一的作用就是存储对象实例，只要保证不断创建对象并且对象不被回收，那么对象数量达到最大堆容量限制后就会产生内存溢出异常了。所以测试的时候把堆的大小固定住并且让堆不可扩展即可。测试代码如下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 package com.xrq.test;
 2 
 3 import java.util.ArrayList;
 4 import java.util.List;
 5 
 6 /**
 7  * 测试内容：堆溢出
 8  *
 9  * 虚拟机参数：-Xms20M -Xmx20M -XX:+HeapDumpOnOutOfMemoryError
10  */
11 public class HeapOverflowTest
12 {
13     public static void main(String[] args)
14     {
15         List<HeapOverflowTest> list = new ArrayList<HeapOverflowTest>();
16         while (true)
17         {
18             list.add(new HeapOverflowTest());
19         }
20     }
21 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
java.lang.OutOfMemoryError: Java heap space
Dumping heap to java_pid8876.hprof ...
Heap dump file created [15782068 bytes in 0.217 secs]
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
    at java.util.Arrays.copyOf(Arrays.java:2760)
    at java.util.Arrays.copyOf(Arrays.java:2734)
    at java.util.ArrayList.ensureCapacity(ArrayList.java:167)
    at java.util.ArrayList.add(ArrayList.java:351)
    at com.xrq.test.HeapOverflowTest.main(HeapOverflowTest.java:18)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

这种异常很常见，也很好发现，因为都提示了“Java **heap** space”了，定位问题的话，根据异常堆栈分析就好了，行号都有指示。解决方案的话，可以调大堆的大小或者从代码上检视是否存在某些对象生命周期过长、持有状态时间过长的情况，长时间少程序运行期间的内存消耗。

 

**栈溢出**

栈内存里面存放基本类型的变量和对象的引用变量。Java虚拟机规范中描述了如果线程请求的栈深度太深（换句话说方法调用的深度太深），就会产生栈溢出了。那么，我们只要写一个无限调用自己的方法，自然就会出现方法调用的深度太深的场景了。测试代码如下

```
 1 package com.xrq.test;
 2 
 3 /**
 4  * 测试内容：栈溢出测试（递归调用导致栈深度不断增加）
 5  * 
 6  * 虚拟机参数：-Xss128k
 7  */
 8 public class StackOverflowTest
 9 {
10     private int stackLength = 1;
11     
12     public void stackLeak()
13     {
14         stackLength++;
15         stackLeak();
16     }
17     
18     public static void main(String[] args) throws Throwable
19     {
20         StackOverflowTest stackOverflow = new StackOverflowTest();
21         try
22         {
23             stackOverflow.stackLeak();
24         }
25         catch (Throwable e)
26         {
27             System.out.println("stack length:" + stackOverflow.stackLength);
28             throw e;
29         }        
30     }
31 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
stack length:1006
Exception in thread "main" java.lang.StackOverflowError
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:14)
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:15)
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:15)
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:15)
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:15)
    at com.xrq.test.StackOverflowTest.stackLeak(StackOverflowTest.java:15)
　　...
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

后面都是一样的，忽略。通过不断创建线程的方式可以产生OutOfMemoryError，因为每个线程都有自己的栈空间。不过这个操作有危险就不做了，原因是Windows平台下，Java的线程是直接映射到操作系统的内核线程上的，如果写个死循环无限产生线程，那么可能会造成操作系统的假死。

上面无限产生线程的场景，从另外一个角度说，就是为每个线程的栈分配的内存空间越大，反而越容易产生内存溢出。其实这也很好理解，操作系统分配给进程的内存是有限制的，比如32位的Windows限制为2GB。虚拟机提供了了参数来控制Java堆和方法区这两部分内存的最大值，剩余内存为2GB-最大堆容量-最大方法区容量，程序计数器很小就忽略了，虚拟机进程本身的耗费也不算，剩下的内存就是栈的了。每个线程分配到的栈容量越大，可建立的线程数自然就越少，建立线程时就越容易把剩下的内存耗尽。

StackOverFlowError这个异常，有错误堆栈可以阅读，比较好定位。而且如果使用虚拟机默认参数，栈深度在大多数情况下，达到1000~2000完全没有问题，正常方法的调用这个深度应该是完全够了。但是如果建立过多线程导致的OutOfMemoryError，在不能减少线程数或者更换64位虚拟机的情况下，就只能通过减小最大堆容量和减小栈容量来换取更多的线程了。

 

**方法区和运行时常量池溢出**

运行时常量池也是方法区的一部分，所以这两个区域一起看就可以了。这个区域的OutOfMemoryError可以利用String.intern()方法来产生。这是一个Native方法，意思是如果常量池中有一个String对象的字符串就返回池中的这个字符串的String对象；否则，将此String对象包含的字符串添加到常量池中去，并且返回此String对象的引用。测试代码如下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 package com.xrq.test;
 2 
 3 import java.util.ArrayList;
 4 import java.util.List;
 5 
 6 /**
 7  * 测试内容：常量池溢出（这个例子也可以说明运行时常量池为方法区的一部分）
 8  * 
 9  * 虚拟机参数-XX:PermSize=10M -XX:MaxPermSize=10M
10  */
11 public class ConstantPoolOverflowTest
12 {
13     public static void main(String[] args)
14     {
15         List<String> list = new ArrayList<String>();
16         int i = 0;
17         while (true)
18         {
19             list.add(String.valueOf(i++).intern());
20         }
21     }
22 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果

```
Exception in thread "Reference Handler" Exception in thread "main" java.lang.OutOfMemoryError: PermGen space
    at java.lang.String.intern(Native Method)
    at com.xrq.test.ConstantPoolOverflowTest.main(ConstantPoolOverflowTest.java:19)
java.lang.OutOfMemoryError: PermGen space
    at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:123)
```

之前有讲过，对于HotSpot而言，方法区=永久代，这里看到OutOfMemoryError的区域是“PermGen space”，即永久代，那其实也就是方法区溢出了。**注意一下JDK1.7下是不会有这个异常的，while循环将一直下去，因为JDK1.7之后溢出了永久代并采用Native Memory来实现方法区的规划了**。