# Java8 以后各个版本的新特性

### 



![summary](https://user-gold-cdn.xitu.io/2019/8/18/16ca4e2bec80dcfa?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



### JDK

JDK 全称 Java Development Kit，是 Java 开发环境。我们通常所说的 JDK 指的是 Java SE (Standard Edition) Development Kit。除此之外还有 Java EE（Enterprise Edition）和 Java ME（Micro Edition platforms）。

### Java 的发布周期

| 版本                  | 发布时间 | 名称       |
| --------------------- | -------- | ---------- |
| JDK Beta              | 1995     | WebRunner  |
| JDK 1.0               | 1996.1   | Oak        |
| JDK 1.1               | 1997.2   |            |
| J2SE 1.2              | 1998.12  | Playground |
| J2SE 1.3              | 2000.5   | Kestrel    |
| J2SE 1.4              | 2002.2   | Merlin     |
| J2SE 5.0              | 2004.9   | Tiger      |
| Java SE 6             | 2006.12  | Mustang    |
| Java SE 7             | 2011.7   | Dolphin    |
| Java SE 8 (LTS)       | 2014.3   |            |
| Java SE 9             | 2017.9   |            |
| Java SE 10 (18.3)     | 2018.3   |            |
| Java SE 11 (18.9 LTS) | 2018.9   |            |
| Java SE 12 (19.3)     | 2019.3   |            |
| Java SE 13 (19.9)     | 2019.9   |            |

下面我们看一些 Java 发展过程中重要的节点。
1995 年 alpha 和 beta Java 公开版本发布，取名为 WebRunner。

1996.1.23 Java 第一个版本发布，取名叫 Oak。但是第一个稳定版本是 JDK 1.0.2，被称做 **Java 1**。

1998.12.8 发布了 J2SE 1.2。这个版本到 J2SE 5.0 更名为 **Java 2**。其中的 SE 指的是 Standard Edition，为了区别于 J2EE（Enterprise Edition）和 J2ME（Micro Edition）。

2000.5 发布了 J2SE 1.3，其中包含了 **HotSpot JVM**。而 HotSpot JVM 首次发布是在 1999.4，名为 J2SE 1.2 JVM。

2004.9.30 发布了 **J2SE 5.0**。为什么这个版本命名和前面几个版本不一样呢？这个版本原本计划以 1.5 命名的，沿用以前的命名方式。但是为了更好的反映这个版本的成熟度，所以改名为 5.0。
这个版本以后，有了一个新的版本控制系统，5.0 用来表示产品版本，用来表示稳定的 J2SE 版本，而 1.5.0 用来表示开发者版本，也就是 Java 5.0 = JDK 1.5.0。

2006.12.11，J2SE **改名为 Java SE**，版本号去掉了 .0。此后对应版本就是 Java 6 = JDK 1.6，Java 7 = JDK 1.7。

2011.7.7. 发布 Java SE 7，是一个重大版本更新。更新了众多特性。

2018.3 发布 Java SE 10。在此之前，Java 基本上是两年一个版本，除了 Java SE 7 经过了五年，Java SE 8 经过了三年。在此之后，就是**每六个月发布一次新版本**。但是不是每个版本都是 LTS（Long-Term-Support）。按照 Oracle 的计划，每三年会有一个 LTS 版本。最近的 LTS 版本就是 Java SE 11 了。

### OpenJDK VS Oracle JDK

OpenJDK 是 在 2007 年由 Sun Corporation（现在的Oracle Corporation） 发布的。是 Oracle JDK 的开源实现版本，以 GPL 协议发布。在 JDK 7 的时候，Sub JDK 就是在 Open JDK 7 的基础上发布的，只替换了少量的源码。在 Sun 公司被 Oracle 收购以后，Sun SDK 就被称为 Oracle JDK。Oracle JDK 是基于 Oracle Binary COde License Agreement 协议。 两者的区别如下：

1. Oracle JDK 将三年发布一次稳定版本，OpenJDK 每三个月发布一次。
2. Oracle JDK 支持 LTS，OpenJDK 只支持当前版本至下一个版本发布。
3. Oracle JDK 采用 Oracle Binary Code License 协议，OpenJDK 采用 GPL v2 协议。
4. Oracle JDK 基于 OpenJDK 构建，技术上基本没有差异。

### Android 和 JDK

说起 Android 和 OpenJDK 的历史渊源，还是略微复杂。 简单来说，Android 最开始使用的 Java 是基于 Apache 协议发布的 Harmony，后来由于 Harmony 本身的限制和 Oracle 公司的起诉，从 Android N 以后， Google 开始使用 OpenJDK。 然后我们再稍微展开聊聊。

#### JVM 和 TCK

Sun 公司最初开发了 Java 语言，同时也开发了 JVM，并且定义了 JVM 规范。这个我们比较清楚，只要基于 JVM 规范开发自己的语言，就可以运行在 JVM 上。但是依照规范开发了语言之后，需要通过 Sun 的 TCK（Technology Compatibility Kit）测试，之后才能成为官方认可的 JVM 语言。

#### Harmony 和 OpenJDK

基于 JVM 规范，Apache 开发了一个开源免费的 Java 实现 Harmony，并且根据 Apache License v2 发布。但是 Sun 公司并没有给 Harmony TCK 许可。

在 2009.4.15 Sun 公司发布了 OpenJDK，基于 GNU GPL 发布。同时 Sun 公司规定只有衍生自 OpenJDK 采用的 GPL 协议的开源实现才能运行 OpenJDK 的 TCK。之后 Oracle 收购 Sun 公司以后接管了 OpenJDK。 由于 Apache 的 Harmony 是 Apache 协议，与 OpenJDK 的 GPL 协议不兼容，所以 Harmony 一直没有得到 TCK 授权。

Android 最开始是采用了 Harmony 作为自己的 Java 类库，因为 Harmony 使用的 Apache 协议更自由。而由于 Harmony 没有通过 TCK 认证，也为后来 Oracle 起诉 Google 埋下伏笔。

#### Oracle 和 Google 关于 JDK 纠纷

后来 Oracle 起诉 Google 主要集中在两点，一是 Oracle 认为 Google 代码中使用了 Java 的 37 个 API，二是 Sun 公司前员工在跳槽后为 Android 项目开发时，直接复制了 OpenJDK 中的九行代码，而 Android 项目并没有按照 GPL 协议授权，所以复制 OpenJDK 代码是没有通过 GPL 授权的。

所以到后来为了解决专利的问题，Android N 以后，Android 开始使用 OpenJDK 替换 Harmony。

以上 Android 和 JDK 参考资料：
[juejin.im/entry/5abc5…](https://juejin.im/entry/5abc516b518825556f557f90)
[zh.wikipedia.org/zh/Android#…](https://zh.wikipedia.org/zh/Android#与甲骨文公司的Java纠纷)
[gudong.name/2019/04/05/…](https://gudong.name/2019/04/05/android-why-java-harmony.html)

聊了一些关于 Java 的历史，下面我们看看各个 Java 版本有那些新特性。这里只列出了对开发者影响比较大的一些特性～

### Java 8

#### 1. Lambda 和 函数式接口

Lambda 表达式相信不用再过多的介绍，终于在 Java 8 引入了，可以极大的减少代码量，代码看起来更清爽。
函数式接口就是*有且仅有一个抽象方法*，但是可以有多个非抽象方法的接口。可以隐式转化为 Lambda 表达式。 我们定义一个函数式接口如下：

```
@FunctionalInterface
interface Operation {
    int operation(int a, int b);
}
复制代码
```

再定义一个 Class 用来操作 Operation 接口。

```
class Test {
    private int operate(int a, int b, Operation operation) {
        return operation.operation(a, b);
    }
}

Test test = new Test();
复制代码
```

在 Java 8 之前，我们想要实现 Operation 接口并传给 Test.operate() 方法使用，我们要定义一个匿名类，实现 Operation 方法。

```
test.operate(1, 2, new Operation() {
    @Override
    public int operation(int a, int b) {
        return a + b;
    }
});
复制代码
```

而使用 Lambda 表达式，我们就可以这样写了：

```
test.operate(1, 2, (a, b) -> a + b);
复制代码
```

#### 2. 方法引用

通过方法引用，可以使用方法的名字来指向一个方法。使用一对冒号来引 "::" 用方法。 还是以上面的例子来看，我们再添加几个方法：

```
@FunctionalInterface
interface Operation {
    int operation(int a, int b);
}

interface Creater<T> {
    T get();
}

interface TestInt {
    int cp(Test test1, Test test2);
}

class Test {
    public static Test create(Creater<Test> creater) {
        return creater.get();
    }

    private int operate(int a, int b, Operation operation) {
        return operation.operation(a, b);
    }

    private static int add(int a, int b) {
        return a + b;
    }

    private int sub(int a, int b) {
        return a - b;
    }

    public int testM(Test test) {
        return 0;
    }

    public void test(TestInt testInt) {
        Test t1 = Test.create(Test::new); 
        Test t2 = Test.create(Test::new);
        testInt.cp(t1, t2);
    }

}
复制代码
```

那么对应的方法引用有四种：
**构造方法引用**
使用方式：Class::new

```
Test test = Test.create(Test::new);
复制代码
```

**静态方法引用**
使用方式：Class::staticMethod

```
test.operate(1, 2, Test::add);
复制代码
```

**对象的实例方法引用**
使用方式：instance::method

```
test.operate(1, 2, test::sub);
复制代码
```

**类的实例方法引用**
使用方式：Class::method

```
test.test(Test::testM);
复制代码
```

其实上面三种方法引用都好理解，最后类的实例方法引用，有两个条件：

1. 首先要满足实例方法，而不是静态方法
2. Lambda 表达式的第一个参数会成为调用实例方法的对象 根据这两点我们看上面的例子，test 方法接受一个 TestInt 实例，用 Lambda 表达式表示就是 (Test t1, Test t2) -> res，而我们调用 test 方法时传入的方法引用是 Test::testM，其参数也是一个 Test 实例，最终 test.test(Test::testM) 的调用效果就是 t1.testM(t2)

#### 3. 接口默认方法和静态方法

Java 8 新增了接口的默认实现，通过 *default* 关键字表示。同时也可以提供静态默认方法。

```
public interface TestInterface {
    String test();

    // 接口默认方法
    default String defaultTest() {
        return "default";
    }

    static String staticTest() {
        return "static";
    }
}
复制代码
```

#### 4. 重复注解

Java 8 支持了重复注解。在 Java 8 之前想实现重复注解，需要用一些方法来绕过限制。比如下面的代码。

```
@interface Author {
    String name();
}

@interface Authors {
    Author[] value();
}

@Authors({@Author(name="a"), @Author(name = "b")})
class Article {
}
复制代码
```

而在 Java 8 中，可以直接用下面的方式。

```
@Repeatable(Authors.class)
@interface Author {
    String name();
}

@interface Authors {
    Author[] value();
}

@Author(name = "a")
@Author(name = "b")
class Article {
}
复制代码
```

在解析注解的时候，Java 8 也提供了新的 API。

```
AnnotatedElement.getAnnotationsByType(Class<T>)
复制代码
```

#### 5. 类型注解

Java 8 之前注解只能用在声明中，在 Java 8 中，注解可以使用在 任何地方。

```
@Author(name="a")
private Object name = "";
private String author = (@Author(name="a")String) name;
复制代码
```

#### 6. 更好的类型推断

Java 8 对于类型推断做了改进。
比如在 Java 7 中下面的写法：

```
List<String> stringList = new ArrayList<>();
stringList.add("A");
stringList.addAll(Arrays.<String>asList());
复制代码
```

在 Java 8 中改进后的写法，可以自动做类型推断。

```
List<String> stringList = new ArrayList<>();
stringList.add("A");
stringList.addAll(Arrays.asList());
复制代码
```

#### 7. Optional

Java 8 中新增了 Optional 类用来解决空指针异常。Optional 是一个可以保存 null 的容器对象。通过 isPresent() 方法检测值是否存在，通过 get() 方法返回对象。
除此之外，Optional 还提供了很多其他有用的方法，具体可以查看[文档](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html)。下面是一些示例代码。

```
// 创建一个 String 类型的容器
Optional<String> str = Optional.of("str");
// 值是否存在
boolean pre = str.isPresent();
// 值如果存在就调用 println 方法，这里传入的是 println 的方法引用
str.ifPresent(System.out::println);
// 获取值
String res = str.get();
// 传入空值
str = Optional.ofNullable(null);
// 如果值存在，返回值，否则返回传入的参数
res = str.orElse("aa");
str = Optional.of("str");
// 如果有值，对其调用映射函数得到返回值，对返回值进行 Optional 包装并返回
res = str.map(s -> "aa" + s).get();
// 返回一个带有映射函数的 Optional 对象
res = str.flatMap(s -> Optional.of(s + "bb")).flatMap(s -> Optional.of(s + "cc")).get();
复制代码
```

#### 8. Stream

Java 8 中新增的 Stream 类提供了一种新的数据处理方式。这种方式将元素集合看做一种流，在管道中传输，经过一系列处理节点，最终输出结果。
关于 Stream 提供的具体方法，可以参照 [API](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html)。下面是一些示例代码。

```
List<String> list = Arrays.asList("maa", "a", "ab", "c");
list.stream()
        .filter(s -> s.contains("a"))
        .map(s -> s + "aa")
        .sorted()
        .forEach(System.out::println);

System.out.println("####");
list.parallelStream().forEach(System.out::println);

List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8);
int res = numbers.stream().map(i -> i + 1).mapToInt(i -> i).summaryStatistics().getMax();
System.out.println(res);
复制代码
```

#### 9. 日期时间 API

Java 8 中新增了日期时间 API 用来加强对日期时间的处理，其中包括了 LocalDate，LocalTime，LocalDateTime，ZonedDateTime 等等，关于 API 可以参照[官方文档](https://www.oracle.com/technetwork/articles/java/jf14-date-time-2125367.html)以及这篇[博客](https://www.cnblogs.com/muscleape/p/9956754.html)，写的很详细。下面是示例代码。

```
LocalDate now = LocalDate.now();
System.out.println(now);
System.out.println(now.getYear());
System.out.println(now.getMonth());
System.out.println(now.getDayOfMonth());

LocalTime localTime = LocalTime.now();
System.out.println(localTime);
LocalDateTime localDateTime = now.atTime(localTime);
System.out.println(localDateTime);
复制代码
```

#### 10. Base64 支持

Java 8 标准库中提供了对 Base 64 编码的支持。具体 API 见可参照[文档](https://docs.oracle.com/javase/8/docs/api/java/util/Base64.html)。下面是示例代码。

```
String base64 = Base64.getEncoder().encodeToString("aaa".getBytes());
System.out.println(base64);
byte[] bytes = Base64.getDecoder().decode(base64);
System.out.println(new String(bytes));
复制代码
```

#### 11. 并行数组 ParallelSort

Java 8 中提供了对数组的并行操作，包括 parallelSort 等等，具体可参照 [API](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html)。

```
Arrays.parallelSort(new int[] {1, 2, 3, 4, 5});
复制代码
```

#### 12. 其他新特性

- 对并发的增强 在java.util.concurrent.atomic包中还增加了下面这些类： DoubleAccumulator DoubleAdder LongAccumulator LongAdder
- 提供了新的 Nashorn javascript 引擎
- 提供了 jjs，是一个给予 Nashorn 的命令行工具，可以用来执行 JavaScript 源码
- 提供了新的类依赖分析工具 jdeps
- JVM 的新特性 JVM内存永久区已经被metaspace替换（JEP 122）。JVM参数 -XX:PermSize 和 –XX:MaxPermSize被XX:MetaSpaceSize 和 -XX:MaxMetaspaceSize代替。

可以看到，Java 8 整体上的改进是很大的，最重要的是引入 Lambda 表达式，简化代码。

其他一些改进可参照 [www.oracle.com/technetwork…](https://www.oracle.com/technetwork/java/javase/8-whats-new-2157071.html)

### Java 9

#### 1. Jigsaw 模块系统

在 Java 9 以前，打包和依赖都是基于 JAR 包进行的。JRE 中包含了 rt.jar，将近 63M，也就是说要运行一个简单的 Hello World，也需要依赖这么大的 jar 包。在 Java 9 中提出的模块化系统，对这点进行了改善。 关于模块化系统具体可以看看这篇[文章](https://zhuanlan.zhihu.com/p/24800180)。

#### 2. JShell REPL

Java 9 提供了交互式解释器。有了 JShell 以后，Java 终于可以像 Python，Node.js 一样在 Shell 中运行一些代码并直接得出结果了。

#### 3. 接口中使用私有方法

Java 9 中可以在接口中定义私有方法。示例代码如下：

```
public interface TestInterface {
    String test();

    // 接口默认方法
    default String defaultTest() {
        pmethod();
        return "default";
    }

    private String pmethod() {
        System.out.println("private method in interface");
        return "private";
    }
}
复制代码
```

#### 4. 集合不可变实例工厂方法

在以前，我们想要创建一个不可变的集合，需要先创建一个可变集合，然后使用 unmodifiableSet 创建不可变集合。代码如下：

```
Set<String> set = new HashSet<>();
set.add("A");
set.add("B");
set.add("C");

set = Collections.unmodifiableSet(set);
System.out.println(set);
复制代码
```

Java 9 中提供了新的 API 用来创建不可变集合。

```
List<String> list = List.of("A", "B", "C");
Set<String> set = Set.of("A", "B", "C");
Map<String, String> map = Map.of("KA", "VA", "KB", "VB");
复制代码
```

#### 5. 改进 try-with-resources

Java 9 中不需要在 try 中额外定义一个变量。Java 9 之前需要这样使用 try-with-resources：

```
InputStream inputStream = new StringBufferInputStream("a");
try (InputStream in = inputStream) {
    in.read();
} catch (IOException e) {
    e.printStackTrace();
}
复制代码
```

在 Java 9 中可以直接使用 inputStream 变量，不需要再额外定义新的变量了。

```
InputStream inputStream = new StringBufferInputStream("a");
try (inputStream) {
    inputStream.read();
} catch (IOException e) {
    e.printStackTrace();
}
复制代码
```

#### 6. 多版本兼容 jar 包

Java 9 中支持在同一个 JAR 中维护不同版本的 Java 类和资源。

#### 7. 增强了 Stream，Optional，Process API

#### 8. 新增 HTTP2 Client

#### 9. 增强 Javadoc，增加了 HTML 5 文档的输出，并且增加了搜索功能

#### 10. 增强 @Deprecated

对 Deprecated 新增了 since 和 forRemoval 属性

#### 11. 增强了钻石操作符 "<>"，可以在 匿名内部类中使用了。

在 Java 9 之前，内部匿名类需要指定泛型类型，如下：

```
Handler<? extends Number> intHandler1 = new Handler<Number>(2) {
}
复制代码
```

而在 Java 9 中，可以自动做类型推导，如下：

```
Handler<? extends Number> intHandler1 = new Handler<>(2) {
}
复制代码
```

#### 12. 多分辨率图像 API：定义多分辨率图像API，开发者可以很容易的操作和展示不同分辨率的图像了。

#### 13. 改进的 CompletableFuture API

CompletableFuture 类的异步机制可以在 ProcessHandle.onExit 方法退出时执行操作。

其他一些改进可参照 [docs.oracle.com/javase/9/wh…](https://docs.oracle.com/javase/9/whatsnew/toc.htm#JSNEW-GUID-C23AFD78-C777-460B-8ACE-58BE5EA681F6)

### Java 10

#### 1. 新增局部类型推断 var

```
var a = "aa";
System.out.println(a);
复制代码
```

var 关键字目前只能用于局部变量以及 for 循环变量声明中。

#### 2. 删除工具 javah

从JDK中移除了 javah 工具，使用 javac -h 代替。

#### 3. 统一的垃圾回收接口，改进了 GC 和其他内务管理

#### 其他特性

- ThreadLocal 握手交互
  JDK 10 引入一种在线程上执行回调的新方法，很方便的停止单个线程而不是停止全部线程或者一个都不停。
- 基于Java的实验性JIT编译器
  Java 10 开启了 Java JIT编译器 Graal，用作Linux / x64平台上的实验性JIT编译器。
- 提供默认的 CA 根证书
- 将 JDK 生态整合到单个仓库
  此JEP的主要目标是执行一些内存管理，并将JDK生态的众多存储库组合到一个存储库中。

其他一些改进可以参照 [www.oracle.com/technetwork…](https://www.oracle.com/technetwork/java/javase/10-relnote-issues-4108729.html#NewFeature)

### Java 11

#### 1. Lambda 表达式中使用 var

```
(var x, var y) -> x.process(y)
复制代码
```

#### 2. 字符串 API 增强

Java 11 新增了 一系列字符串处理方法，例如：

```
// 判断字符串是否为空白
" ".isBlank(); 
" Javastack ".stripTrailing();  // " Javastack"
" Javastack ".stripLeading();   // "Javastack "
复制代码
```

#### 3. 标准化 HttpClient API

#### 4. java 命令直接编译并运行 java 文件，省去先 javac 编译生成 class 再运行的步骤

#### 5. 增加对 TLS 1.3 的支持

其他一些改进可以参照 [www.oracle.com/technetwork…](https://www.oracle.com/technetwork/java/javase/11-relnote-issues-5012449.html#NewFeature)

### Java 12

#### switch 表达式

Java 12 以后，switch 不仅可以作为语句，也可以作为表达式。

```
private String switchTest(int i) {
    return switch (i) {
        case 1 -> "1";
        default -> "0";
    };
}
复制代码
```

其他一些改进可以参照 [www.oracle.com/technetwork…](https://www.oracle.com/technetwork/java/javase/12-relnote-issues-5211422.html#NewFeature)

### 总结



![summary1](https://user-gold-cdn.xitu.io/2019/8/18/16ca4e326c3132c8?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)