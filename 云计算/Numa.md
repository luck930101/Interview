## NUMA是什么

【非统一内存访问（NUMA）是一种用于多处理器的电脑记忆体设计，内存访问时间取决于处理器的内存位置。 在NUMA下，处理器访问它自己的本地存储器的速度比非本地存储器（存储器的地方到另一个处理器之间共享的处理器或存储器）快一些。】

下图就描述了一个比较形象的NUMA架构：

![这里写图片描述](https://s5.51cto.com/wyfs02/M02/00/A7/wKiom1mbuTPhVBNhAAAeAlaf1X8837.png-wh_651x-s_558380355.png)

我们有两个NUMA结点。每个NUMA结点有一些CPU, 一个内部总线，和自己的内存，甚至可以有自己的IO。每个CPU有离自己最近的内存可以直接访问。所以，使用NUMA架构，系统的性能会更快。在NUMA结构下，我们可以比较方便的增加CPU的数目。而在非NUMA架构下，增加CPU会导致系统总线负载很重，性能提升不明显。
每个CPU也可以访问另外NUMA结点上的内存，但是这样的访问，速度会比较慢。我们要尽量避免。应用软件如果没有意识到这种结构，在NUMA机器上，有时候性能会更差，这是因为，他们经常会不自觉的去访问远端内存导致性能下降。

## NUMA的几个概念（Socket，Core，Thread , Node）

![这里写图片描述](https://img-blog.csdn.net/20150512112954867?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvdXN0Y19keWxhbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

总结：

- Socket就是主板上的CPU插槽;

- Core就是socket里独立的一组程序执行的硬件单元，比如寄存器，计算单元等;

- Thread：就是超线程hyperthread的概念，逻辑的执行单元，独立的执行上下文，但是共享core内的寄存器和计算单元。

  NUMA体系结构中多了Node的概念，这个概念其实是用来解决core的分组的问题，具体参见下图来理解（图中的OS CPU可以理解thread，那么core就没有在图中画出），从图中可以看出每个Socket里有两个node，共有4个socket，每个socket 2个node，每个node中有8个thread，总共4（Socket）× 2（Node）× 8 （4core × 2 Thread） = 64个thread。

![这里写图片描述](https://img-blog.csdn.net/20170903141112192?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMTU0Mzc2Mjk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

根据上面提到的，由于每个node内部有自己的CPU总线和内存，所以如果一个虚拟机的vCPU跨不同的Node的话，就会导致一个node中的CPU去访问另外一个node中的内存的情况，这就导致内存访问延迟的增加。在有些特殊场景下，比如NFV环境中，对性能有比较高的要求，就非常需要同一个虚拟机的vCPU尽量被分配到同一个Node中的pCPU上。

## 如何查看机器的NUMA拓扑结构

比较常用的命令就是lscpu，具体输出如下：

```
dylan@hp3000:~$ lscpu   
Architecture:          x86_64  
CPU op-mode(s):        32-bit, 64-bit  
Byte Order:            Little Endian  
CPU(s):                48                                       //共有48个逻辑CPU（threads）  
On-line CPU(s) list:   0-47  
Thread(s) per core:    2                               //每个core有2个threads  
Core(s) per socket:    6                                //每个socket有6个cores  
Socket(s):             4                                      //共有4个sockets  
NUMA node(s):          4                               //共有4个NUMA nodes  
Vendor ID:             GenuineIntel  
CPU family:            6  
Model:                 45  
Stepping:              7  
CPU MHz:               1200.000  
BogoMIPS:              4790.83  
Virtualization:        VT-x  
L1d cache:             32K                           //L1 data cache 32k  
L1i cache:             32K                            //L1 instruction cache 32k  （牛x机器表现，冯诺依曼+哈弗体系结构）  
L2 cache:              256K  
L3 cache:              15360K  
NUMA node0 CPU(s):     0-5,24-29        
NUMA node1 CPU(s):     6-11,30-35  
NUMA node2 CPU(s):     12-17,36-41  
NUMA node3 CPU(s):     18-23,42-47  
```