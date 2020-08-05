Error类和Exception类的父类都是throwable类，他们的区别是：

Error类一般是指与虚拟机相关的问题，如系统崩溃，虚拟机错误，内存空间不足，方法调用栈溢等。对于这类错误的导致的应用程序中断，仅靠程序本身无法恢复和预防，遇到这样的错误，建议让程序终止。
 Exception类表示程序可以处理的异常，可以捕获且可能恢复。遇到这类异常，应该尽可能处理异常，使程序恢复运行，而不应该随意终止异常。
 Exception类又分为运行时异常（Runtime Exception）和受检查的异常(Checked Exception )，运行时异常;ArithmaticException,IllegalArgumentException，编译能通过，但是一运行就终止了，程序不会处理运行时异常，出现这类异常，程序会终止。而受检查的异常，要么用try。。。catch捕获，要么用throws字句声明抛出，交给它的父类处理，否则编译不会通过。

**①.Exception（异常）是应用程序中可能的可预测、可恢复问题。**一般大多数异常表示中度到轻度的问题。异常一般是在特定环境下产生的，通常出现在代码的特定方法和操作中。在 EchoInput 类中，当试图调用 readLine 方法时，可能出现 IOException 异常。
 Exception 类有一个重要的子类 RuntimeException。RuntimeException 类及其子类表示“JVM 常用操作”引发的错误。例如，若试图使用空值对象引用、除数为零或数组越界，则分别引发运行时异常（NullPointerException、ArithmeticException）和 ArrayIndexOutOfBoundException。
 **②.Error（错误）**表示运行应用程序中较严重问题。大多数错误与代码编写者执行的操作无关，而表示代码运行时 JVM（Java 虚拟机）出现的问题。例如，当 JVM 不再有继续执行操作所需的内存资源时，将出现 OutOfMemoryError。
 检查异常 和 未检查异常 的划分

**Java中的异常分为两大类：**
 1.Checked Exception（非Runtime Exception）
 2.Unchecked Exception（Runtime Exception）

 **运行时异常**
 RuntimeException类是Exception类的子类，它叫做运行时异常，Java中的所有运行时异常都会直接或者间接地继承自RuntimeException类。
 Java中凡是继承自Exception，而不继承自RuntimeException类的异常都是非运行时异常。
 一个try后面可以跟多个catch，但不管多少个，最多只会有一个catch块被执行。
 对于非运行时异常（checked exception），必须要对其进行处理，否则无法通过编译。

 **处理方式有两种：**
 1.使用try..catch..finally进行捕获；
 2.在产生异常的方法声明后面写上throws 某一个Exception类型，如throws Exception，将异常抛出到外面一层去。
 对于运行时异常（runtime exception），可以对其进行处理，也可以不处理。推荐不对运行时异常进行处理。
 扩展：错误和异常的区别(Error vs Exception)

 **1).java.lang.Error:** Throwable的子类，用于标记严重错误。合理的应用程序不应该去try/catch这种错误。绝大多数的错误都是非正常的，就根本不该出现的。
 java.lang.Exception: Throwable的子类，用于指示一种合理的程序想去catch的条件。即它仅仅是一种程序运行条件，而非严重错误，并且鼓励用户程序去catch它。

 **2).Error和RuntimeException **及其子类都是未检查的异常（unchecked exceptions），而所有其他的Exception类都是检查了的异常（checked exceptions）.
 checked exceptions: 通常是从一个可以恢复的程序中抛出来的，并且最好能够从这种异常中使用程序恢复。比如FileNotFoundException, ParseException等。检查了的异常发生在编译阶段，必须要使用try…catch（或者throws）否则编译不通过。

 **unchecked exceptions: **通常是如果一切正常的话本不该发生的异常，但是的确发生了。发生在运行期，具有不确定性，主要是由于程序的逻辑问题所引起的。比如ArrayIndexOutOfBoundException, ClassCastException等。从语言本身的角度讲，程序不该去catch这类异常，虽然能够从诸如RuntimeException这样的异常中catch并恢复，但是并不鼓励终端程序员这么做，因为完全没要必要。因为这类错误本身就是bug，应该被修复，出现此类错误时程序就应该立即停止执行。 因此，面对Errors和unchecked exceptions应该让程序自动终止执行，程序员不该做诸如try/catch这样的事情，而是应该查明原因，修改代码逻辑。

 **RuntimeException：**RuntimeException体系包括错误的类型转换、数组越界访问和试图访问空指针等等。
 处理RuntimeException的原则是：如果出现 RuntimeException，那么一定是程序员的错误。例如，可以通过检查数组下标和数组边界来避免数组越界访问异常。其他（IOException等等）checked异常一般是外部错误，例如试图从文件尾后读取数据等，这并不是程序本身的错误，而是在应用环境中出现的外部错误。
 以上这篇Java_异常类(错误和异常,两者的区别介绍) 就是小编分享给大家的全部内容了，希望能给大家一个参考，也希望大家多多支持脚本之家。
 常见的异常;
 ArrayIndexOutOfBoundsException 数组下标越界异常，
 ArithmaticException 算数异常 如除数为零
 NullPointerException 空指针异常
 IllegalArgumentException 不合法参数异常