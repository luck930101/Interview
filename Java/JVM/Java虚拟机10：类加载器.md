**类与类加载器**

虚拟机设计团队把类加载阶段张的"通过一个类的全限定名来获取此类的二进制字节流"这个动作放到Java虚拟机外部去实现，以便让应用程序自己决定如何去获取所需要的类。实现这个动作的代码模块称为"类加载器"。类加载器虽然只用于实现类的加载动作，但它在Java程序中起到的作用却远远不限定于类加载阶段。对于任意一个类，都需要由加载它的类加载器和这个类本身一同确立其在Java虚拟机中的唯一性，每一个类加载器，都拥有一个独立的类名称空间。这句话表达地再简单一点就是：**比较两个类是否"相等"，只有在这两个类是由同一个类加载器加载的前提下才有意义**，否则即使这两个类来源于同一个.class文件，被同一个虚拟机加载，只要加载它们的类加载器不同，这两个类必定不相等。

上面说的"相等"，包括代表类的.class对象的equals()方法、isAssignableFrom()方法、isInstance()方法的返回结果，也包括使用instanceof关键字做对象所属关系判定等情况。

 

**类加载器模型**

从Java虚拟机的角度讲，只有两种不同的类加载器：启动类加载器Bootstrap ClassLoader，这个类加载器是由C++语言实现的，是虚拟机自身的一部分；其他类加载器，这些类加载器都由Java语言实现，独立于虚拟机外部，并且全部继承自java.lang.ClassLoader。从开发人员的角度讲，类加载器还可以划分地更加细致一些，一张图就能说明：

![img](https://images2015.cnblogs.com/blog/801753/201509/801753-20150928224102605-1436171001.png)

关于这张图首先说两点：

1、这三个层次的类加载器并不是继承关系，而只是层次上的定义

2、它并不是一个强制性的约束模型，而是Java设计者推荐给开发者的一种类加载器实现方式

OK，然后一个一个类加载器来看：

1、启动类加载器Bootstrap ClassLoader

之前说过了这是一个嵌在JVM内核中的加载器。它负责加载的是JAVA_HOME/lib下的类库，系统类加载器无法被Java程序直接应用

2、扩展类加载器Extension ClassLoader

这个类加载器由sun.misc.Launcher$ExtClassLoader实现，它负责用于加载JAVA_HOME/lib/ext目录中的，或者被java.ext.dirs系统变量指定所指定的路径中所有类库，开发者可以直接使用扩展类加载器。java.ext.dirs系统变量所指定的路径的可以通过程序来查看

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class TestMain
{
    public static void main(String[] args)
    {
        System.out.println(System.getProperty("java.ext.dirs"));
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果

```
E:\MyEclipse10\Common\binary\com.sun.java.jdk.win32.x86_64_1.6.0.013\jre\lib\ext;C:\Windows\Sun\Java\lib\ext
```

3、应用程序类加载器Application ClassLoader

这个类加载器由sun.misc.Launcher$AppClassLoader实现。这个类也一般被称为系统类加载器，写个小程序看下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class TestMain
{
    public static void main(String[] args)
    {
        System.out.println(ClassLoader.getSystemClassLoader());
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果为：

```
sun.misc.Launcher$AppClassLoader@546b97fd
```

看到通过"ClassLoader.getSystemClassLoader"，得到的是sun.misc.Launcher$AppClassLoader，这也证明了JDK认为Application ClassLoader是系统类加载器。顺便根据类加载器模型，打印一下这个类的父加载器：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class TestMain
{
    public static void main(String[] args)
    {
        System.out.println(ClassLoader.getSystemClassLoader().getParent());
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果为：

```
sun.misc.Launcher$ExtClassLoader@535ff48b
```

看出Application ClassLoader的父加载器确实是Extension ClassLoader，符合图中的模型。那么再打印父加载器呢？按照我们的想法应该是Bootstrap ClassLoader了，看下是不是：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class TestMain
{
    public static void main(String[] args)
    {
        System.out.println(ClassLoader.getSystemClassLoader().getParent().getParent());
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果为：

```
null
```

这会打印出来的是null了。其实也很好理解，Bootstrap ClassLoader以外的ClassLoader都是Java实现的，因此这些ClassLoader势必在Java堆中有一份实例在，所以Extension ClassLoader和Application ClassLoader都能打印出内容来。但是Bootstrap ClassLoader是JVM的一部分，是用C/C++写的，不属于Java，自然在Java堆中也没有自己的空间，所以就返回null了。所以，**如果ClassLoader得到的是null，那么表示的ClassLoader就是Bootstrap ClassLoader**。

另外要说很重要的一点，反编译一下rt.jar，找到sun.misc.Launcher看一下Application ClassLoader的实现：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 static class AppClassLoader extends URLClassLoader
 2   {
 3     public static ClassLoader getAppClassLoader(final ClassLoader paramClassLoader)
 4       throws IOException
 5     {
 6       String str = System.getProperty("java.class.path");
 7       final File[] arrayOfFile = str == null ? new File[0] : Launcher.getClassPath(str);
 8       return (ClassLoader)AccessController.doPrivileged(new PrivilegedAction()
 9       {
10         public Launcher.AppClassLoader run()
11         {
12           URL[] arrayOfURL = this.val$s == null ? new URL[0] : Launcher.pathToURLs(arrayOfFile);
13           return new Launcher.AppClassLoader(arrayOfURL, paramClassLoader);
14         }
15       });
16     }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

重点就在第6行，Application ClassLoader只会加载java.class.path下的.class文件，java.class.path代表的是什么路径？打印一下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
public class TestMain
{
    public static void main(String[] args)
    {
        System.out.println(System.getProperty("java.class.path"));
    }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

运行结果为：

```
F:\代码\MyEclipse\TestArticle\bin;F:\学习\第三方jar包\XStream\xstream-1.4.jar;F:\学习\第三方jar包\XStream\kxml2.jar
```

我这里有添加两个.jar到CLASSPATH下。那也可以下一个重要的结论了：

**Application ClassLoader只能加载项目bin目录下的.class文件**。

 

**双亲委派模型**

最后讲一下双亲委派模型，其实上面的类加载器模型图就是一个双亲委派模式的图，这里把它再讲清楚一点。

双亲委派模型是在JDK1.2期间被引入的，其工作过程可以分为两步：

1、**如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成，每一个层次的类加载器都是如此。**

2、**只有当父加载器反馈自己无法完成这这个加载请求（它的搜索范围中没有找到所需的类）时，子加载器才会尝试自己去加载**

所以，其实所有的加载请求最终都应该传送到顶层的启动类加载器中。双亲委派模型对于Java程序的稳定运作很重要，因为Java类随着它的加载器一起具备了一种带有优先级的层次关系。例如java.lang.Object，存放于rt.jar中，无论哪一个类加载器要去加载这个类，最终都是由Bootstrap ClassLoader去加载，因此Object类在程序的各种类加载器环境中都是一个类。相反，如果没有双亲委派模型，由各个类自己去加载的话，如果用户自己编写了一个java.lang.Object，并放在CLASSPATH下，那系统中将会出现多个不同的Object类，Java体系中最基础的行为也将无法保证，应用程序也将会变得一片混乱。