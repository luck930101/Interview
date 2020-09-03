当*JVM*（*Java*虚拟机）启动时，会形成由三个类加载器组成的初始类加载器层次结构：

 

**bootstrap classloader**

*|*

**extension classloader**

*|*

**system classloader**

 

*bootstrap classloader* －引导（也称为原始）类加载器，它负责加载*Java*的核心类。在*Sun*的*JVM*中，在执行*java*的命令中使用*-Xbootclasspath*选项或使用*- D*选项指定*sun.boot.class.path*系统属性值可以指定附加的类。这个加载器的是非常特殊的，它实际上不是 *java.lang.ClassLoader*的子类，而是由*JVM*自身实现的。大家可以通过执行以下代码来获得*bootstrap classloader*加载了那些核心类库：

*URL[] urls=sun.misc.Launcher.getBootstrapClassPath().getURLs();*

*for (int i = 0; i < urls.length; i++) {*

*System.out.println(urls.toExternalForm());*

*}*

在我的计算机上的结果为：

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/dom.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/sax.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/xalan-2.3.1.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/xercesImpl-2.0.0.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/xml-apis.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/endorsed/xsltc.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/rt.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/i18n.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/sunrsasign.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/jsse.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/jce.jar*

*file:/C:/j2sdk1.4.1_01/jre/lib/charsets.jar*

*file:/C:/j2sdk1.4.1_01/jre/classes*

这时大家知道了为什么我们不需要在系统属性*CLASSPATH*中指定这些类库了吧，因为*JVM*在启动的时候就自动加载它们了。

 

*extension classloader* －扩展类加载器，它负责加载*JRE*的扩展目录（*JAVA_HOME/jre/lib/ext*或者由*java.ext.dirs*系统属性指定的）中*JAR*的类包。这为引入除*Java*核心类以外的新功能提供了一个标准机制。因为默认的扩展目录对所有从同一个*JRE*中启动的*JVM*都是通用的，所以放入这个目录的 *JAR*类包对所有的*JVM*和*system classloader*都是可见的。在这个实例上调用方法*getParent()*总是返回空值*null*，因为引导加载器*bootstrap classloader*不是一个真正的*ClassLoader*实例。所以当大家执行以下代码时：

*System.out.println(System.getProperty("java.ext.dirs"));*

*ClassLoader extensionClassloader=ClassLoader.getSystemClassLoader().getParent();*

*System.out.println("the parent of extension classloader : "+extensionClassloader.getParent());*

结果为：

*C:/j2sdk1.4.1_01/jre/lib/ext*

*the parent of extension classloader : null*

*extension classloader*是*system classloader*的*parent*，而*bootstrap classloader*是*extension classloader*的*parent*，但它不是一个实际的*classloader*，所以为*null*。

 

*system classloader* －系统（也称为应用）类加载器，它负责在*JVM*被启动时，加载来自在命令*java*中的*-classpath*或者*java.class.path*系统属性或者 *CLASSPATH*操作系统属性所指定的*JAR*类包和类路径。总能通过静态方法*ClassLoader.getSystemClassLoader()*找到该类加载器。如果没有特别指定，则用户自定义的任何类加载器都将该类加载器作为它的父加载器。执行以下代码即可获得：

*System.out.println(System.getProperty("java.class.path"));*

输出结果则为用户在系统属性里面设置的*CLASSPATH*。

*classloader* 加载类用的是全盘负责委托机制。所谓全盘负责，即是当一个*classloader*加载一个*Class*的时候，这个*Class*所依赖的和引用的所有 *Class*也由这个*classloader*负责载入，除非是显式的使用另外一个*classloader*载入；委托机制则是先让*parent*（父）类加载器 *(*而不是*super*，它与*parent classloader*类不是继承关系*)*寻找，只有在*parent*找不到的时候才从自己的类路径中去寻找。此外类加载还采用了*cache*机制，也就是如果 *cache*中保存了这个*Class*就直接返回它，如果没有才从文件中读取和转换成*Class*，并存入*cache*，这就是为什么我们修改了*Class*但是必须重新启动*JVM*才能生效的原因。

 

 

每个*ClassLoader*加载*Class*的过程是：

*1.*检测此*Class*是否载入过（即在*cache*中是否有此*Class*），如果有到*8,*如果没有到*2*

*2.*如果*parent classloader*不存在（没有*parent*，那*parent*一定是*bootstrap classloader*了），到*4*

*3.*请求*parent classloader*载入，如果成功到*8*，不成功到*5*

*4.*请求*jvm*从*bootstrap classloader*中载入，如果成功到*8*

*5.*寻找*Class*文件（从与此*classloader*相关的类路径中寻找）。如果找不到则到*7.*

*6.*从文件中载入*Class*，到*8.*

*7.*抛出*ClassNotFoundException.*

*8.*返回*Class.*

 

其中*5.6*步我们可以通过覆盖*ClassLoader*的*findClass*方法来实现自己的载入策略。甚至覆盖*loadClass*方法来实现自己的载入过程。

 

类加载器的顺序是：

先是*bootstrap classloader*，然后是*extension classloader*，最后才是*system classloader*。大家会发现加载的*Class*越是重要的越在靠前面。这样做的原因是出于安全性的考虑，试想如果*system classloader“*亲自*”*加载了一个具有破坏性的*“java.lang.System”*类的后果吧。这种委托机制保证了用户即使具有一个这样的类，也把它加入到了类路径中，但是它永远不会被载入，因为这个类总是由*bootstrap classloader*来加载的。大家可以执行一下以下的代码：

*System.out.println(System.class.getClassLoader());*

将会看到结果是*null*，这就表明*java.lang.System*是由*bootstrap classloader*加载的，因为*bootstrap classloader*不是一个真正的*ClassLoader*实例，而是由*JVM*实现的，正如前面已经说过的。

 

下面就让我们来看看*JVM*是如何来为我们来建立类加载器的结构的：

*sun.misc.Launcher*，顾名思义，当你执行*java*命令的时候，*JVM*会先使用*bootstrap classloader*载入并初始化一个*Launcher*，执行下来代码：

*System.out.println("the Launcher's classloader is "+sun.misc.Launcher.getLauncher().getClass().getClassLoader());*

结果为：

*the Launcher's classloader is null (*因为是用*bootstrap classloader*加载*,*所以*class loader*为*null)*

*Launcher* 会根据系统和命令设定初始化好*class loader*结构，*JVM*就用它来获得*extension classloader*和*system classloader,*并载入所有的需要载入的*Class*，最后执行*java*命令指定的带有静态的*main*方法的*Class*。*extension classloader*实际上是*sun.misc.Launcher$ExtClassLoader*类的一个实例，*system classloader*实际上是*sun.misc.Launcher$AppClassLoader*类的一个实例。并且都是 *java.net.URLClassLoader*的子类。

 

让我们来看看*Launcher*初试化的过程的部分代码。

 

*Launcher*的部分代码：

*public class Launcher {*

*public Launcher() {*

*ExtClassLoader extclassloader;*

*try {*

*//*初始化*extension classloader*

*extclassloader = ExtClassLoader.getExtClassLoader();*

*} catch(IOException ioexception) {*

*throw new InternalError("Could not create extension class loader");*

*}*

*try {*

*//*初始化*system classloader*，*parent*是*extension classloader*

*loader = AppClassLoader.getAppClassLoader(extclassloader);*

*} catch(IOException ioexception1) {*

*throw new InternalError("Could not create application class loader");*

*}*

*//*将*system classloader*设置成当前线程的*context classloader*（将在后面加以介绍）

*Thread.currentThread().setContextClassLoader(loader);*

*......*

*}*

*public ClassLoader getClassLoader() {*

*//*返回*system classloader*

*return loader;*

*}*

*}*

 

*extension classloader*的部分代码：

*static class Launcher$ExtClassLoader extends URLClassLoader {*

 

*public static Launcher$ExtClassLoader getExtClassLoader()*

*throws IOException*

*{*

*File afile[] = getExtDirs();*

*return (Launcher$ExtClassLoader)AccessController.doPrivileged(new Launcher$1(afile));*

*}*

*private static File[] getExtDirs() {*

*//*获得系统属性*“java.ext.dirs”*

*String s = System.getProperty("java.ext.dirs");*

*File afile[];*

*if(s != null) {*

*StringTokenizer stringtokenizer = new StringTokenizer(s, File.pathSeparator);*

*int i = stringtokenizer.countTokens();*

*afile = new File;*

*for(int j = 0; j < i; j++)*

*afile[j] = new File(stringtokenizer.nextToken());*

 

*} else {*

*afile = new File[0];*

*}*

*return afile;*

*}*

*}*

 

*system classloader*的部分代码：

*static class Launcher$AppClassLoader extends URLClassLoader*

*{*

 

*public static ClassLoader getAppClassLoader(ClassLoader classloader)*

*throws IOException*

*{*

*//*获得系统属性*“java.class.path”*

*String s = System.getProperty("java.class.path");*

*File afile[] = s != null ? Launcher.access$200(s) : new File[0];*

*return (Launcher$AppClassLoader)AccessController.doPrivileged(new Launcher$2(s, afile, classloader));*

*}*

*}*

 

看了源代码大家就清楚了吧，*extension classloader*是使用系统属性*“java.ext.dirs”*设置类搜索路径的，并且没有*parent*。*system classloader*是使用系统属性*“java.class.path”*设置类搜索路径的，并且有一个*parent classloader*。*Launcher*初始化*extension classloader*，*system classloader*，并将*system classloader*设置成为*context classloader*，但是仅仅返回*system classloader*给*JVM*。

 

　　这里怎么又出来一个*context classloader*呢？它有什么用呢？我们在建立一个线程*Thread*的时候，可以为这个线程通过*setContextClassLoader*方法来指定一个合适的*classloader*作为这个线程的*context classloader*，当此线程运行的时候，我们可以通过*getContextClassLoader*方法来获得此*context classloader*，就可以用它来载入我们所需要的*Class*。默认的是*system classloader*。利用这个特性，我们可以*“*打破*”classloader*委托机制了，父*classloader*可以获得当前线程的*context classloader*，而这个*context classloader*可以是它的子*classloader*或者其他的*classloader*，那么父*classloader*就可以从其获得所需的 *Class*，这就打破了只能向父*classloader*请求的限制了。这个机制可以满足当我们的*classpath*是在运行时才确定*,*并由定制的 *classloader*加载的时候*,*由*system classloader(*即在*jvm classpath*中*)*加载的*class*可以通过*context classloader*获得定制的*classloader*并加载入特定的*class(*通常是抽象类和接口*,*定制的*classloader*中是其实现*),*例如*web*应用中的*servlet*就是用这种机制加载的*.*

 

 

好了，现在我们了解了*classloader*的结构和工作原理，那么我们如何实现在运行时的动态载入和更新呢？只要我们能够动态改变类搜索路径和清除*classloader*的*cache*中已经载入的*Class*就行了，有两个方案，一是我们继承一个*classloader*，覆盖 *loadclass*方法，动态的寻找*Class*文件并使用*defineClass*方法来；另一个则非常简单实用，只要重新使用一个新的类搜索路径来*new* 一个*classloader*就行了，这样即更新了类搜索路径以便来载入新的*Class*，也重新生成了一个空白的*cache(*当然*,*类搜索路径不一定必须更改*)*。噢，太好了，我们几乎不用做什么工作，*java.netURLClassLoader*正是一个符合我们要求的*classloader*！我们可以直接使用或者继承它就可以了！

 

这是*j2se1.4 API*的*doc*中*URLClassLoader*的两个构造器的描述：

*URLClassLoader(URL[] urls)*

*Constructs a new URLClassLoader for the specified URLs using the default delegation parent ClassLoader.*

*URLClassLoader(URL[] urls, ClassLoader parent)*

*Constructs a new URLClassLoader for the given URLs.*

其中*URL[] urls*就是我们要设置的类搜索路径，*parent*就是这个*classloader*的*parent classloader*，默认的是*system classloader*。

 

 

好，现在我们能够动态的载入*Class*了，这样我们就可以利用*newInstance*方法来获得一个*Object*。但我们如何将此*Object*造型呢？可以将此*Object*造型成它本身的*Class*吗？

 

首先让我们来分析一下*java*源文件的编译，运行吧！*javac*命令是调用*“JAVA_HOME/lib/tools.jar”*中的*“com.sun.tools.javac.Main”*的*compile*方法来编译：

 

*public static int compile(String as[]);*

 

*public static int compile(String as[], PrintWriter printwriter);*

 

返回*0*表示编译成功，字符串数组*as*则是我们用*javac*命令编译时的参数，以空格划分。例如：

*javac -classpath c:/foo/bar.jar;. -d c:/ c:/Some.java*

则字符串数组*as*为*{"-classpath","c://foo//bar.jar;.","-d","c://","c://Some.java"}*，如果带有*PrintWriter*参数，则会把编译信息出到这个指定的*printWriter*中。默认的输出是*System.err*。

 

其中*Main*是由*JVM*使用*Launcher*初始化的*system classloader*载入的，根据全盘负责原则，编译器在解析这个*java*源文件时所发现的它所依赖和引用的所有*Class*也将由*system classloader*载入，如果*system classloader*不能载入某个*Class*时，编译器将抛出一个*“cannot resolve symbol”*错误。

 

所以首先编译就通不过，也就是编译器无法编译一个引用了不在*CLASSPATH*中的未知*Class*的*java*源文件，而由于拼写错误或者没有把所需类库放到*CLASSPATH*中，大家一定经常看到这个*“cannot resolve symbol”*这个编译错误吧！

 

其次，就是我们把这个*Class*放到编译路径中，成功的进行了编译，然后在运行的时候不把它放入到*CLASSPATH*中而利用我们自己的 *classloader*来动态载入这个*Class*，这时候也会出现*“java.lang.NoClassDefFoundError”*的违例，为什么呢？

 

我们再来分析一下，首先调用这个造型语句的可执行的*Class*一定是由*JVM*使用*Launcher*初始化的*system classloader*载入的，根据全盘负责原则，当我们进行造型的时候，*JVM*也会使用*system classloader*来尝试载入这个*Class*来对实例进行造型，自然在*system classloader*寻找不到这个*Class*时就会抛出*“java.lang.NoClassDefFoundError”*的违例。

 

*OK*，现在让我们来总结一下，*java*文件的编译和*Class*的载入执行，都是使用*Launcher*初始化的*system classloader*作为类载入器的，我们无法动态的改变*system classloader*，更无法让*JVM*使用我们自己的*classloader*来替换*system classloader*，根据全盘负责原则，就限制了编译和运行时，我们无法直接显式的使用一个*system classloader*寻找不到的*Class*，即我们只能使用*Java*核心类库，扩展类库和*CLASSPATH*中的类库中的*Class*。

 

还不死心！再尝试一下这种情况，我们把这个*Class*也放入到*CLASSPATH*中，让*system classloader*能够识别和载入。然后我们通过自己的*classloader*来从指定的*class*文件中载入这个*Class*（不能够委托 *parent*载入，因为这样会被*system classloader*从*CLASSPATH*中将其载入），然后实例化一个*Object*，并造型成这个*Class*，这样*JVM*也识别这个*Class*（因为 *system classloader*能够定位和载入这个*Class*从*CLASSPATH*中），载入的也不是*CLASSPATH*中的这个*Class*，而是从 *CLASSPATH*外动态载入的，这样总行了吧！十分不幸的是，这时会出现*“java.lang.ClassCastException”*违例。

 

为什么呢？我们也来分析一下，不错，我们虽然从*CLASSPATH*外使用我们自己的*classloader*动态载入了这个*Class*，但将它的实例造型的时候是*JVM*会使用*system classloader*来再次载入这个*Class*，并尝试将使用我们的自己的*classloader*载入的*Class*的一个实例造型为*system classloader*载入的这个*Class*（另外的一个）。大家发现什么问题了吗？也就是我们尝试将从一个*classloader*载入的*Class*的一个实例造型为另外一个*classloader*载入的*Class*，虽然这两个*Class*的名字一样，甚至是从同一个*class*文件中载入。但不幸的是*JVM* 却认为这个两个*Class*是不同的，即*JVM*认为不同的*classloader*载入的相同的名字的*Class*（即使是从同一个*class*文件中载入的）是不同的！这样做的原因我想大概也是主要出于安全性考虑，这样就保证所有的核心*Java*类都是*system classloader*载入的，我们无法用自己的*classloader*载入的相同名字的*Class*的实例来替换它们的实例。

 

看到这里，聪明的读者一定想到了该如何动态载入我们的*Class*，实例化，造型并调用了吧！

 

那就是利用面向对象的基本特性之一的多形性。我们把我们动态载入的*Class*的实例造型成它的一个*system classloader*所能识别的父类就行了！这是为什么呢？我们还是要再来分析一次。当我们用我们自己的*classloader*来动态载入这我们只要把这个*Class*的时候，发现它有一个父类*Class*，在载入它之前*JVM*先会载入这个父类*Class*，这个父类*Class*是*system classloader*所能识别的，根据委托机制，它将由*system classloader*载入，然后我们的*classloader*再载入这个*Class*，创建一个实例，造型为这个父类*Class*，注意了，造型成这个父类 *Class*的时候（也就是上溯）是面向对象的*java*语言所允许的并且*JVM*也支持的，*JVM*就使用*system classloader*再次载入这个父类*Class*，然后将此实例造型为这个父类*Class*。大家可以从这个过程发现这个父类*Class*都是由 *system classloader*载入的，也就是同一个*class loader*载入的同一个*Class*，所以造型的时候不会出现任何异常。而根据多形性，调用这个父类的方法时，真正执行的是这个*Class*（非父类 *Class*）的覆盖了父类方法的方法。这些方法中也可以引用*system classloader*不能识别的*Class*，因为根据全盘负责原则，只要载入这个*Class*的*classloader*即我们自己定义的 *classloader*能够定位和载入这些*Class*就行了。

 

这样我们就可以事先定义好一组接口或者基类并放入*CLASSPATH*中，然后在执行的时候动态的载入实现或者继承了这些接口或基类的子类。还不明白吗？让我们来想一想*Servlet*吧，*web application server*能够载入任何继承了*Servlet*的*Class*并正确的执行它们，不管它实际的*Class*是什么，就是都把它们实例化成为一个*Servlet Class*，然后执行*Servlet*的*init*，*doPost*，*doGet*和*destroy*等方法的*,*而不管这个*Servlet*是从*web- inf/lib*和*web-inf/classes*下由*system classloader*的子*classloader(*即定制的*classloader)*动态载入。说了这么多希望大家都明白了。在*applet,ejb*等容器中*,*都是采用了这种机制*.*

 

*classloader*虽然称为类加载器，但并不意味着只能用来加载*Class*，我们还可以利用它也获得图片，音频文件等资源的 *URL*，当然，这些资源必须在*CLASSPATH*中的*jar*类库中或目录下。我们来看*API*的*doc*中关于*ClassLoader*的两个寻找资源和 *Class*的方法描述吧： *public URL getResource(String name)* 用指定的名字来查找资源，一个资源是一些能够被*class*代码访问的在某种程度上依赖于代码位置的数据（图片，音频，文本等等）。

一个资源的名字是以*'/'*号分隔确定资源的路径名的。

这个方法将先请求*parent classloader*搜索资源，如果没有*parent*，则会在内置在虚拟机中的*classloader*（即*bootstrap classloader*）的路径中搜索。如果失败，这个方法将调用*findResource(String)*来寻找资源。

*public static URL getSystemResource(String name)*

从用来载入类的搜索路径中查找一个指定名字的资源。这个方法使用*system class loader*来定位资源。即相当于*ClassLoader.getSystemClassLoader().getResource(name)*。

 

例如：

*System.out.println(ClassLoader.getSystemResource("java/lang/String.class"));*

的结果为：

*jar:file:/C:/j2sdk1.4.1_01/jre/lib/rt.jar!/java/lang/String.class*

表明*String.class*文件在*rt.jar*的*java/lang*目录中。

因此可以将图片等资源随同*Class*一同打包到*jar*类库中（当然，也可单独打包这些资源）并添加它们到*class loader*的搜索路径中，我们就可以无需关心这些资源的具体位置，让*class loader*来帮我们寻找了！