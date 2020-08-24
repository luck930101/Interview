**一、SQL注入简介**

所谓SQL注入，就是通过把SQL命令插入到Web[表单](http://baike.baidu.com/item/表单)提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。

具体来说，它是利用现有应用程序，将（恶意的）SQL命令注入到后台数据库引擎执行的能力，它可以通过在Web表单中输入（恶意）SQL语句得到一个存在安全漏洞的网站上的数据库，而不是按照设计者意图去执行SQL语句。

   SQL注入是比较常见的网络攻击方式之一，它不是利用[操作系统](http://lib.csdn.net/base/operatingsystem)的BUG来实现攻击，而是针对程序员编程时的疏忽，通过SQL语句，实现无帐号登录，甚至篡改[数据库](http://lib.csdn.net/base/mysql)。

**二、SQL注入攻击的总体思路**



​    1.永远不要信任用户的输入，要对用户的输入进行校验，可以通过正则表达式，或限制长度，对单引号和双"-"进行转换等。

​    2.永远不要使用动态拼装SQL，可以使用参数化的SQL或者直接使用存储过程进行数据查询存取。

​    3.永远不要使用管理员权限的数据库连接，为每个应用使用单独的权限有限的数据库连接。

​    4.不要把机密信息明文存放，请加密或者hash掉密码和敏感的信息。

​    5.应用的异常信息应该给出尽可能少的提示，最好使用自定义的错误信息对原始错误信息进行包装，把异常信息存放在独立的表中。

**三、SQL注入攻击实例**

  比如在一个登录界面，要求输入用户名和密码：

  可以这样输入实现免帐号登录：

  用户名： ‘or 1 = 1 –

  密 码：

  点登陆,如若没有做特殊处理,那么这个非法用户就很得意的登陆进去了.(当然现在的有些语言的数据库API已经处理了这些问题)

  这是为什么呢? 下面我们分析一下：

  从理论上说，后台认证程序中会有如下的SQL语句：

  String sql = "select * from user_table where username=

  ' "+userName+" ' and password=' "+password+" '";

  当输入了上面的用户名和密码，上面的SQL语句变成：

  SELECT * FROM user_table WHERE username=

  '’or 1 = 1 -- and password='’

  分析SQL语句：

  条件后面username=”or 1=1 用户名等于 ” 或1=1 那么这个条件一定会成功；

  然后后面加两个-，这意味着注释，它将后面的语句注释，让他们不起作用，这样语句永远都能正确执行，用户轻易骗过系统，获取合法身份。

  这还是比较温柔的，如果是执行

  SELECT * FROM user_table WHERE

  username='' ;DROP DATABASE (DB Name) --' and password=''

  ….其后果可想而知…

 

**四、应对方法**

  下面我针对JSP，说一下应对方法：

  **1.（简单又有效的方法）PreparedStatement**

  采用预编译语句集，它内置了处理SQL注入的能力，只要使用它的setXXX方法传值即可。

  使用好处：

  (1).代码的可读性和可维护性.

  (2).PreparedStatement尽最大可能提高性能.

  (3).最重要的一点是极大地提高了安全性.

  原理：

  sql注入只对sql语句的准备(编译)过程有破坏作用

  而PreparedStatement已经准备好了,执行阶段只是把输入串作为数据处理,

  而不再对sql语句进行解析,准备,因此也就避免了sql注入问题.

 

**2.使用正则表达式过滤传入的参数**

  要引入的包：

  import [Java](http://lib.csdn.net/base/javase).util.regex.*;

  正则表达式：

  private String CHECKSQL = “^(.+)\\sand\\s(.+)|(.+)\\sor(.+)\\s$”;

  判断是否匹配：

  Pattern.matches(CHECKSQL,targerStr);

  下面是具体的正则表达式：

  检测SQL meta-characters的正则表达式 ：

  /(\%27)|(\’)|(\-\-)|(\%23)|(#)/ix

  修正检测SQL meta-characters的正则表达式 ：/((\%3D)|(=))[^\n]*((\%27)|(\’)|(\-\-)|(\%3B)|(:))/i

  典型的SQL 注入攻击的正则表达式 ：/\w*((\%27)|(\’))((\%6F)|o|(\%4F))((\%72)|r|(\%52))/ix

  检测SQL注入，UNION查询关键字的正则表达式 ：/((\%27)|(\’))union/ix(\%27)|(\’)

  检测MS SQL Server SQL注入攻击的正则表达式：

  /exec(\s|\+)+(s|x)p\w+/ix

  等等…..

 

**3.字符串过滤**

  比较通用的一个方法：

 （||之间的参数可以根据自己程序的需要添加）

  public static boolean sql_inj(String str)

  {

  String inj_str = "'|and|exec|insert|select|delete|update|

  count|*|%|chr|mid|master|truncate|char|declare|;|or|-|+|,";

  String inj_stra[] = split(inj_str,"|");

  for (int i=0 ; i &lt; inj_stra.length ; i++ )

  {

   if (str.indexOf(inj_stra[i])&gt;=0)

   {

​    return true;

   }

  }

  return false;

  }

 

**4.jsp中调用该函数检查是否包函非法字符**

 

  防止SQL从URL注入：

  sql_inj.java代码：

 

  package sql_inj;

  import java[.NET](http://lib.csdn.net/base/dotnet).*;

  import java.io.*;

  import java.sql.*;

  import java.text.*;

  import java.lang.String;

  public class sql_inj{

  public static boolean sql_inj(String str)

  {

   String inj_str = "'|and|exec|insert|select|delete|update|

   count|*|%|chr|mid|master|truncate|char|declare|;|or|-|+|,";

   //这里的东西还可以自己添加

   String[] inj_stra=inj_str.split("\\|");

   for (int i=0 ; i &lt; inj_stra.length ; i++ )

​    {

​     if (str.indexOf(inj_stra[i])&gt;=0)

​     {

​      return true;

​     }

​    }

​    return false;

​    }

  }

 

**5.JSP页面判断代码：**

 

  使用[JavaScript](http://lib.csdn.net/base/javascript)在客户端进行不安全字符屏蔽

  功能介绍：检查是否含有”‘”,”\\”,”/”

  参数说明：要检查的字符串

  返回值：0：是1：不是

  函数名是

  function check(a)

  {

   return 1;

   fibdn = new Array (”‘” ,”\\”,”/”);

   i=fibdn.length;

   j=a.length;

   for (ii=0; ii＜i; ii++)

   { for (jj=0; jj＜j; jj++)

   { temp1=a.charAt(jj);

​    temp2=fibdn[ii];

​    if (tem’; p1==temp2)

​    { return 0; }

​    }

​    }

​    return 1;

​    }

===================================



  此外Druid数据库连接池中的WallFilter，用于防止sql注入
<bean id="wall-filter-config" class="com.alibaba.druid.wall.WallConfig" init-method="init">
        <!-- 指定配置装载的目录  -->
        <property name="dir" value="META-INF/druid/wall/mysql" />
     </bean>
<bean id="wall-filter" class="com.alibaba.druid.wall.WallFilter">
        <property name="dbType" value="mysql" />
        <property name="config" ref="wall-filter-config" />
    </bean>
  <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
      ...
       <property name="proxyFilters">
          <list>
              <ref bean="wall-filter"/>
          </list>
       </property>
    </bean>

总的说来，防范一般的SQL注入只要在代码规范上下点功夫就可以了。

凡涉及到执行的SQL中有变量时，用JDBC（或者其他数据持久层）提供的如：PreparedStatement就可以 ，切记不要用拼接字符串的方法就可以了。

