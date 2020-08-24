jvm包括三种类加载器：

第一种：bootstrap classloader：加载java的核心类。

第二种：extension classloader：负责加载jre的扩展目录中的jar包。

第三种：它负责在*JVM*被启动时，加载来自在命令*java*中的*-classpath*或者*java.class.path*系统属性或者 *CLASSPATH*操作系统属性所指定的*JAR*类包和类路径。

以上参考博客原文路径为：http://blog.csdn.net/xrt95050/article/details/4413998

jvm 加载包名和类名相同的类时，先加载classpath中jar路径放在前面的，包名类名都相同，那jvm没法区分了，如果使用ide一般情况下是会提示发生冲突而报错，若不报错，只有第一个包被引入（在classpath路径下排在前面的包），第二个包会在classloader加载类时判断重复而忽略。



如果加载包名和类型相同的类可以使用不同的类加载器，也就是说使用自定义类加载器加载同包同名的类。

