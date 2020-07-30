这篇总结一下Java中static关键字的作用与用法。

参考文献如下：

- [[java\]static关键字的四种用法](https://www.cnblogs.com/dotgua/p/6354151.html)
- [Java中static关键字的作用](https://blog.csdn.net/zhouseawater/article/details/53582945)
- [Java中的static关键字解析](http://www.cnblogs.com/dolphin0520/p/3799052.html)
- [Java中static关键字的作用](https://blog.csdn.net/jsqfengbao/article/details/44724219)

下面直接分析static关键字的四种基本用法。

## 修饰成员变量

平时的使用当中，static最常用的功能就是修饰类的属性和方法，让他们成为类的成员属性和方法，我们通常将用static修饰的成员称为类成员、静态成员或者静态变量。

静态变量属于类，在内存中只有一个复制，只要静态变量所在的类被加载，这个静态变量就会被分配空间，因此就可以被使用了。

要理解上面这句话，首先要明白Java语言中内存管理的机制。Java把内存分成两种，一种叫做栈内存，一种叫做堆内存。具体区别如下：

- 在函数中定义的一些基本类型的变量和对象的引用变量都是在函数的栈内存中分配。当在一段代码块中定义一个变量时，java就在栈中为这个变量分配内存空间，当超过变量的作用域后，java会自动释放掉为该变量分配的内存空间，该内存空间可以立刻被另作他用。
- 堆内存用于存放由new创建的对象和数组。在堆中分配的内存，由java虚拟机自动垃圾回收器来管理。在堆中产生了一个数组或者对象后，还可以在栈中定义一个特殊的变量，这个变量的取值等于数组或者对象在堆内存中的首地址，在栈中的这个特殊的变量就变成了数组或者对象的引用变量，以后就可以在程序中使用栈内存中的引用变量来访问堆中的数组或者对象，引用变量相当于为数组或者对象起的一个别名，或者代号。

JVM是基于堆栈的虚拟机.JVM为每个新创建的线程都分配一个堆栈.也就是说,对于一个Java程序来说，它的运行就是通过对堆栈的操作来完成的。堆栈以帧为单位保存线程的状态。JVM对堆栈只进行两种操作:以帧为单位的压栈和出栈操作。

每一个Java应用都唯一对应一个JVM实例，每一个实例唯一对应一个堆。应用程序在运行中所创建的所有类实例或数组都放在这个堆中,并由应用所有的线程共享.跟C/C++不同，Java中分配堆内存是自动初始化的。Java中所有对象的存储空间都是在堆中分配的，但是这个对象的引用却是在堆栈中分配,也就是说在建立一个对象时从两个地方都分配内存，在堆中分配的内存实际建立这个对象，而在堆栈中分配的内存只是一个指向这个堆对象的指针(引用)而已。

堆中有一个特殊的区域，静态储存区。由于每一个对象都是通过new操作符，在堆中划出一块内存储存对象的。而不管由一个类实例化了多少对象，这些对象都由同一个类实例化来的，那么静态储存区就储存了类的定义，当我们通过new来生成对象时，会根据这里定义的类的定义去创建对象。

明白了这一点之后，通过staic关键字修饰的成员变量也是存放在静态储存区中的。所以，如果类的静态成员变量发生了改变，那么由该类实例化的所有对象的该静态成员变量也会发生相同的改变。

对静态变量的引用有两种方式：

- 类.静态变量
- 对象.静态变量

所以，可以发现，静态变量无需实例化对象，直接通过类名即可访问。而没有static修饰的成员变量，则需要首先由类实例化对象，再通过对象访问该成员变量才可以。

此外，当成员变量使用了static修饰，该变量不再被对象所管理，而统一交由类管理，如果某一个对象对静态成员变量产生修改，那么其他所有对象的静态成员变量也会发生相应修改。这样会让该属性变得难以控制。这时可以用private修饰。

## 修饰成员方法

static的另一个作用，就是修饰成员方法。相比于修饰成员属性，修饰成员方法对于数据的存储上面并没有多大的变化，因为我们从上面可以看出，方法本来就是存放在类的定义当中的。

static修饰成员方法最大的作用，就是可以使用”类名.方法名”的方式操作方法，避免了先要new出对象的繁琐和资源消耗，我们可能会经常在帮助类中看到它的使用：

```
public class PrintHelper {

    public static void print(Object o){
        System.out.println(o);             //调用了静态方法
    }

    public static void main(String[] args) {
        PrintHelper.print("Hello world");  //调用了静态方法
    }
}12345678910
```

从上面的例子，不难发现：使得static修饰的方法成为类的方法，使用时通过“类名.方法名”的方式就可以方便的使用了，相当于定义了一个全局的函数（只要导入该类所在的包即可）。所以，相应的，非静态方法则还是要通过实例化对象，再通过“对象.方法名”的方式访问了。

进一步，由于静态方法可以直接通过类名调用，说明调用静态方法的时候，是不存在对象的，所以，静态方法中不能有this与super关键字！并且由于这个特性，在静态方法中不能访问类的非静态成员变量和非静态成员方法，因为非静态成员方法/变量都是必须依赖具体的对象才能够被调用，即使存在类实例化的对象，也不清楚具体调用哪一个对象的非静态成员变量或者方法。

静态方法只能访问所属类的静态成员变量和成员方法。

但是反过来，非静态方法是可以访问静态方法与静态成员变量的。

## 单例设计模式

static一个很重要的用途就是实现单例设计模式。

单例设计模式的特点是该类只能有一个实例，为了实现这一功能，必须隐藏类的构造函数，即把构造函数声明为private，并提供一个创建对象的方法，由于构造对象被声明为private，外界无法直接创建这个类型的对象，只能通过该类提供的方法来获取类的对象，要达到这样的目的只能把创建对象的方法声明为static，程序实例如下：

```
class Singleton{
    private static Singleton instance = null;
    private Singleton(){}
    public static getInstance(){
        if(instance == null){
            instance = new Singleton();
        }
        return instance;
    }
}12345678910
```

## 静态块

static关键字还有一个比较关键的作用就是 用来形成静态代码块以优化程序性能。static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。

为什么说static块可以用来优化程序性能，是因为它的特性:只会在类加载的时候执行一次。

举个例子：

```
class Person{
    private Date birthDate;

    public Person(Date birthDate) {
        this.birthDate = birthDate;
    }

    boolean isBornBoomer() {
        Date startDate = Date.valueOf("1946");
        Date endDate = Date.valueOf("1964");
        return birthDate.compareTo(startDate)>=0 && birthDate.compareTo(endDate) < 0;
    }
}12345678910111213
```

isBornBoomer是用来这个人是否是1946-1964年出生的，而每次isBornBoomer被调用的时候，都会生成startDate和birthDate两个对象，造成了空间浪费，如果改成这样效率会更好：

```
class Person{
    private Date birthDate;
    private static Date startDate,endDate;

    static{
        startDate = Date.valueOf("1946");
        endDate = Date.valueOf("1964");
    }

    public Person(Date birthDate) {
        this.birthDate = birthDate;
    }

    boolean isBornBoomer() {
        return birthDate.compareTo(startDate)>=0 && birthDate.compareTo(endDate) < 0;
    }
}1234567891011121314151617
```

## 静态导包

用import static代替import静态导入包是JDK1.5中的新特性。

一般我们导入一个类都用 import com…..ClassName;而静态导入是这样：import static com…..ClassName. * ;这里的多了个static，还有就是类名ClassName后面多了个.* ，意思是导入这个类里的静态方法。当然，也可以只导入某个静态方法，只要把 .* 换成静态方法名就行了。然后在这个类中，就可以直接用方法名调用静态方法，

这种方法的好处就是可以简化一些操作，例如打印操作System.out.println(…);就可以将其写入一个静态方法print(…)，在使用时直接print(…)就可以了。

但是这种方法建议在有很多重复调用的时候使用，如果仅有一到两次调用，不如直接写来的方便.

在静态导入之前：

```
public class Singleton {
    public static void main(String [] args){
        System.out.println(Integer.MAX_VALUE);
        System.out.println(Integer.toHexString(36));
    }
}123456
```

在静态导入之后：

```
import static java.lang.System.out;
import static java.lang.Integer.*;

public class Singleton {
    public static void main(String [] args){
        out.println(MAX_VALUE);
        out.println(Integer.toHexString(36));
    }
}
```