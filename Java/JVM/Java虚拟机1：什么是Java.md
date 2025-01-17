**前言**

让我们来看一下Java的广告词，来自http://www.java.com/zh_CN/about/：

- 97%的企业桌面运行Java
- 美国有89%的桌面（或计算机）运行Java
- 全球有900万Java开发人员
- 开发人员的头号选择
- 排名第一的部署平台
- 有30亿部移动电话运行Java
- 100%的蓝光盘播放器附带了Java
- 有50亿张Java卡在使用
- 1.25亿台TV设备运行Java
- 前5个原始设备制造商均提供了Java ME

很牛逼不是吗？OK，这么牛逼的背后，我们Java开发人员有想过每天和我们朝夕相处的Java到底是什么呢？当然，很多人脑海里第一反应一定是，Java不就是一门编程语言吗，咱们每天写代码的语言啊。当然，这么说也是对的，只是Java实际包含的面更广，一起往下来看下。

 

**什么是Java**

经过了多年的发展，Java早已由一门单纯的计算机编程语言，演变为了一套强大的**技术体系。**是的，什么是Java，我想技术体系四个字应该是最好的概括了吧。Java设计者们将Java划分为3种结构独立但却彼此依赖的技术体系分支，它们分别对应着不同的规范集合和组件：

1、Java SE（标准版），主要活跃在桌面领域，主要包含了Java API组件。

2、Java EE（企业版），活跃在企业级领域，除了包含Java API组件外，还扩充有Web组件、事务组件、分布式组件、EJB组件、消息组件等，综合这些技术，开发人员完全可以构建出一个具备高性能、结构严谨的企业级应用，并且Java EE也是用于构建SOA（面向服务架构）的首选平台。

3、Java ME（精简版），活跃在嵌入式领域，称之为精简版的原因是，它仅保留了Java API中的部分组件，以及适应设备的一些特有组件。

上面讲到Java技术体系的分支，那既然Java是一种技术体系，我们来看一下组成这种技术体系的技术：

1、Java编程语言

2、字节码

3、Java API，包括Java API类库和来自商业机构以及开源社区的第三方类库

4、Java虚拟机

很多时候我们只关注了第一点，因为第一点才是和工作切实相关的。Java技术体系所包含的内容实际上Java官方有提供给我们一张图，图片来源http://docs.oracle.com/javase/7/docs/

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150921165309834-1573432020.png)

 

**Java的优点**

Java能获得如此广泛的认可，除了它拥有一门结构严谨、面向对象的编程语言之外，还有许多不可忽视的优点：

1、它摆脱了硬件平台的束缚，实现了“一次编写、到处运行”

2、它提供了一个相对安全的内存管理和访问机制，避免了绝大部分的内存泄露和指针越界问题

3、它实现了热点代码检测和运行时编译及优化，这使得Java应用能随着运行时间的增加而获得更高的性能

4、它有一套完整的应用程序接口，还有无数来自商业机构和开源社区的第三方类库来帮助它实现各种各样的功能

5、它与身俱来对分布式技术的支持就比较完善

但是，Java最大的优势和财富还不是以上这些，就像高翔龙老师在《Java虚拟机精讲》中写的，Java真正强大的地方是因为拥有全世界最多的技术拥护者和开源社区支持，他们无时无刻都保持着最充沛的体力与思维，一步一步地驱动着Java技术的走向。

 

**JDK和JRE**

两个常见的重要概念。其实上面的图中已经划分出了JDK和JRE的范围了。我们对这张图做一个归纳，用我们的语言简单地总结一下什么是JDK和JRE：

1、JDK（Java Development Kit），是用于支持Java程序开发的最小环境，基本上Java程序设计语言、Java虚拟机、Java API类库这三部分组成了JDK

2、JRE（Java Runtime Enviroment）,是支持Java程序运行的标准环境，Java API类库中的Java SE API自己和Java虚拟机这两部分组成了JRE

 

**OpenJDK**

前面有讲过，“**Java真正强大的地方是因为拥有全世界最多的技术拥护者和开源社区支持，他们无时无刻都保持着最充沛的体力与思维，一步一步地驱动着Java技术的走向**”。其实JDK在一开始并不是开源的，但是随着开源运动的蓬勃发展，2006年Sun公司宣布将对Java开放源代码，开源的Java平台开发主要集中在OpenJDK项目上。2009年4月15日，Sun公司正式发布OpenJDK，JDK 7则是Java开源后发布的第一个版本，任何组织和个人都可以为Java的发展做出贡献。当然OpenJDK和真正的Oracle JDK（因为Sun公司被Oracle公司在2010年收购了嘛，所以就叫做Oracle JDK了）还是有区别的：

OpenJDK中的代码基本上都来自于Oracle JDK，属于Oracle JDK的一个分支，但是其中去除了一些非开源的组件和代码，替换成了开源的组件和代码，主要是加密和图形的部分。因此用OpenJDK代替Oracle JDK可能会有一些的不兼容。

对于OpenJDK感兴趣的，可以在OpenJDK官网http://download.java.net/openjdk/jdk7/下载OpenJDK的源代码。像Java虚拟机HotSpot、Java编译器Javac、JNI等等，源代码都在里面。

 

**JCP和JSR**

JCP（Java Community Process）是一套制定Java技术规范的机制，通过制定和审查JSR（Java Specification Requests）推动Java技术规范的发展。一个已经提交的JSR要想成为最终状态，需要经过正式的公开审查，并由JCP委员会投票决定，最终的JSR会提供一个参考实现，它是免费而且公开源代码的。JSR并非只由Oracle管理，任何个人都可以注册并参与审查JSR，对于Java语言发展动态感兴趣的人来说，跟踪JSR的动态发展是一条不错的学习途径。在JCP官网http://www.jcp.org/中可以查看所有的JSR，下面列举几个大家熟悉的JSR：

1、JSR 14，泛型

2、JSR 51，NIO

3、JSR 175，注解

4、JSR 201，枚举以及自动装箱等

5、JSR 221，JDBC4.0 API

 

**Java虚拟机**

最后，轮到这个大哥登场，也是之后文章的主角。为什么Java可以实现所谓的“一次编写，到处运行”，主要是因为虚拟机的存在。Java虚拟机负责Java程序设计语言的安全特性和平台无关性。Java虚拟机屏蔽了与具体操作系统平台相关的信息，使得Java语言编译器只需要生成在Java虚拟机上运行的字节码，就可以在多种平台上不加修改地运行。Java虚拟机使得Java摆脱了具体机器的束缚，使跨越不同平台编写程序成为了可能。

要多提一句，我们现在说的Java虚拟机基本上都是JDK自带的虚拟机HotSpot，这款虚拟机也是目前商用虚拟中市场份额最大的一款虚拟机，可以通过在命令行程序中输入“java -version”来查看：

<img src="https://images2015.cnblogs.com/blog/801753/201509/801753-20150921175053740-1046515521.png">

那其实市面上还有很多别的优秀的虚拟机。Sun公司除了有大名鼎鼎的HotSpot外，还有KVM、Squawk VM、Maxine VM，BEA公司有JRockit VM、IBM公司有J9 VM等等。

**后记**

越学习Java虚拟机，越觉得它有意思，工作中越能解决一些复杂的、奇怪的、别人解决不了的问题（为什么你比别人厉害、为什么你比别人拿更高的工资？说白了不就是你能解决别人解决不了的问题、做到别人做不到的事吗？）。又或者，当一个Java项目庞大到一定程度之后，就会根据自己的业务需求，定制自己的虚拟机，比如淘宝网就基于OpenJDK深度定制了Taobao VM，能做到这一点的基础就是对Java虚拟机有深入的理解。作为一个Java开发，如果目标只是把写代码这件事情做好，那么OK，完全不需要去学习、研究Java语言之外的任何东西，每到一个公司，只要简单理解公司项目的整体架构以及理清业务就好了。但是如果目标是成为一名Java技术专家、CTO，相信代码可以改变世界（至少我本人是朝着这个方向努力的），那么学习、研究虚拟机绝对是不可缺少的一课。