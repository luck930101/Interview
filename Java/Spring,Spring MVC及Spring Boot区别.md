> 对于一个Java开发者来说，Spring可谓如雷贯耳，无论是Spring框架，还是Spring引领的IOC，AOP风格，都对后续Java开发产生的深远的影响，同时，Spring社区总能及时响应开发者的需求，推出适应潮流发展的新功能特定；而对于大部分开发者而言，平时接触最多的应该就是Spring MVC以及Spring Boot了，本文将分别对Spring，Spring MVC以及Spring Boot做总体概述，并分析阐述它们各自想要解决的问题，以便初学者能更好的了解Spring及相关概念

# 本篇结构

本篇将大致分为下列四个部分

- 什么是Spring？它解决了什么问题？
- 什么是Spring MVC？它解决了什么问题？
- 什么是Spring Boot？它解决了什么问题？
- Spring，Spring MVC，Spring Boot 三者比较

# 什么是Spring？它解决了什么问题？

我们说到Spring，一般指代的是Spring Framework，它是一个开源的应用程序框架，提供了一个简易的开发方式，**通过这种开发方式，将避免那些可能致使代码变得繁杂混乱的大量的业务/工具对象，说的更通俗一点就是由框架来帮你管理这些对象，包括它的创建，销毁等**，比如基于Spring的项目里经常能看到的`Bean`，它代表的就是由Spring管辖的对象。

而在被管理对象与业务逻辑之间，Spring通过IOC（控制反转）架起使用的桥梁，IOC也可以看做Spring最核心最重要的思想，通过IOC能带来什么好处呢？首先来看一个实际开发中的典型应用场景，假设我们有一个基于MVC分层结构的应用，通过controller层对外提供接口，而通过service层提供具体的实现，在service层中有一个`WelcomeService`服务接口，一般情况下都是通过`WelcomeService service = new WelcomeServiceImpl();`创建实例并进行调用：



```java
public class WelcomeController {
    private WelcomeService service = new WelcomeServiceImpl();

    @RequestMapping("/welcome")
    public String welcome() {
    return service.retrieveWelcomeMessage();
    }
}
```

调用后发现一切正常，此时，功能提交，需要进行测试，而由于实际应用环境与测试环境有所区别，需要替换`WelcomeServiceImpl`为一个`MockWelcomeServiceImpl`，以方便测试，怎么办？没有其他办法，只有改代码：



```cpp
public class WelcomeController {
    private WelcomeService service = new MockWelcomeServiceImpl();

    ...
}
```

测试OK后再将代码改回去，这种方式太过于繁琐，且对代码的侵入性很强；
 下面看通过Spring的IOC如何实现，首先将`WelcomeService`交由Spring管理：



```csharp
<bean name="WelcomeService" class="XXX.XXX.XXX.service.impl.WelcomeServiceImpl"/>
```

然后在业务代码处通过Spring IOC拿到具体对象：



```kotlin
public class WelcomeController {
    @Autowired
    private WelcomeService service;

    @RequestMapping("/welcome")
    public String welcome() {
        return service.retrieveWelcomeMessage();
    }
}
```

测试的时候，只需要更改配置文件，将`WelcomeService`对应的实现改为`MockWelcomeServiceImpl`即可：



```csharp
<bean name="WelcomeService" class="XXX.XXX.XXX.service.impl.MockWelcomeServiceImpl"/>
```

这种方式对业务代码没有任何侵入，**它有效的实现松耦合**，大家都知道紧耦合的代码是业务发展的噩梦；同时，Spring IOC提供的远不止这些，如通过单例减少创建无用的对象，通过延迟加载优化初始化成本等

当然，Spring 的核心功能远不知这些，如：

- Spring AOP
- Spring JDBC
- Spring MVC
- Spring ORM
- Spring JMS
- Spring Test

其实不通过Spring框架依然可以实现这些功能特定，但是Spring 提供了更优雅的抽象接口以方便对这些功能的组装，同时又给予每个具体实现以灵活的配置；另外，基于Spring，你可以方便的与其他框架进行集成，如`hibernate`，`ibatis`等，Spring官方的原则是绝不重复造轮子，有好的解决方案只需要通过Spring进行集成即可。**纵览Spring的结构，你会发现Spring Framework 本身并未提供太多具体的功能，它主要专注于让你的项目代码组织更加优雅，使其具有极好的灵活性和扩展性，同时又能通过Spring集成业界优秀的解决方案**，想了解Spring的核心实现机制可参考[tiny spring 项目](https://github.com/code4craft/tiny-spring)

# 什么是Spring MVC？它解决了什么问题？

Spring MVC是Spring的一部分，Spring 出来以后，大家觉得很好用，于是按照这种模式设计了一个 MVC框架（一些用Spring 解耦的组件），**主要用于开发WEB应用和网络接口，它是Spring的一个模块，通过Dispatcher Servlet, ModelAndView 和 View Resolver，让应用开发变得很容易**，一个典型的Spring MVC应用开发分为下面几步：
 首先通过配置文件声明Dispatcher Servlet：



```xml
    <servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>com.qgd.oms.web.common.mvc.OmsDispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/applicationContext.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
```

通过配置文件声明servlet详情，如MVC resource，data source，bean等



```xml
    <mvc:resources mapping="/css/**/*" location="/static/css/" cache-period="21600"/>
    <mvc:resources mapping="/js/**/*" location="/static/js/" cache-period="21600"/>
    <mvc:resources mapping="/views/**/*.html" location="/static/views/" cache-period="21600"/>
    <mvc:resources mapping="/fonts/**/*" location="/static/fonts/"/>
    <mvc:resources mapping="/ueditor/**/*" location="/static/js/lib/ueditor/"/>
    <mvc:resources mapping="/img/**/*" location="/static/img/"/>

    <bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource" destroy-method="close">
        <property name="driverClassName" value="${jdbc.driver}"/>
        <property name="url" value="${jdbc.url}"/>
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
        <property name="validationQuery" value="${jdbc.validationQuery}"/>
        <property name="maxTotal" value="10"/>
        <property name="minIdle" value="5"/>
        <property name="maxIdle" value="10"/>
        <property name="defaultAutoCommit" value="true"/>
        <property name="testWhileIdle" value="true"/>
        <property name="testOnBorrow" value="true"/>
        <property name="poolPreparedStatements" value="true"/>
        <property name="maxOpenPreparedStatements" value="50"/>
    </bean>

    <bean id="configService" class="com.qgd.oms.web.common.service.ConfigService">
        <property name="configStore">
            <bean class="com.qgd.oms.web.common.service.impl.DbConfigStore">
                <property name="dataSource" ref="dataSource"/>
                    <property name="taskScheduler" ref="defaultScheduler"/>
                <property name="refreshInterval" value="30000"/>
            </bean>
        </property>
    </bean>
```

若需添加其它功能，如security，则需添加对应配置：



```xml
    <http pattern="/css/**/*" security="none"/>
    <http pattern="/js/**/*" security="none"/>
    <http pattern="/views/**/*.html" security="none"/>
    <http pattern="/fonts/**/*" security="none"/>
    <http pattern="/ueditor/**/*" security="none"/>
    <http pattern="/img/**/*" security="none"/>

    <http use-expressions="true" entry-point-ref="omsAuthenticationEntryPoint">
        <logout logout-url="/omsmc/authentication/logout/*" success-handler-ref="omsLogoutSuccessHandler"></logout>
        <intercept-url pattern='/omsmc/authentication/login*' access="permitAll" />
        <intercept-url pattern='/ms/**/*' access="permitAll" />
        <intercept-url pattern='/**' access="authenticated" />
        <!--<security:form-login />-->
        <custom-filter ref="omsUsernamePasswordAuthenticationFilter" position="FORM_LOGIN_FILTER" />
        <remember-me services-ref="omsRememberMeServices" key="yfboms"/>
        <csrf disabled="true"/>
    </http>
```

增加业务代码，如controller，service，model等，最后生成war包，通过容器进行启动

# 什么是Spring Boot？它解决了什么问题？

初期的Spring通过代码加配置的形式为项目提供了良好的灵活性和扩展性，但随着Spring越来越庞大，其配置文件也越来越繁琐，太多复杂的xml文件也一直是Spring被人诟病的地方，特别是近些年其他简洁的WEB方案层出不穷，如基于Python或Node.Js，几行代码就能实现一个WEB服务器，对比起来，大家渐渐觉得Spring那一套太过繁琐，此时，Spring社区推出了Spring Boot，它的目的在于**实现自动配置，降低项目搭建的复杂度**，如需要搭建一个接口服务，通过Spring Boot，几行代码即可实现，请看代码示例：



```jsx
//引入spring-boot-starter-web依赖
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```



```java
//声明Spring Boot应用，直接写业务逻辑即可
@Controller
@SpringBootApplication
public class MockServerApplication {
    @RequestMapping("/hi")
    @ResponseBody
    String home() {
        return "how are you!";
    }

    public static void main(String[] args) {
        SpringApplication.run(MockServerApplication.class, args);
    }
}
```

你甚至都不用额外的WEB容器，直接生成jar包执行即可，因为`spring-boot-starter-web`模块中包含有一个内置tomcat，可以直接提供容器使用；基于Spring Boot，不是说原来的配置没有了，而是Spring Boot有一套默认配置，我们可以把它看做比较通用的约定，而Spring Boot遵循的也是**约定优于配置**原则，同时，如果你需要使用到Spring以往提供的各种复杂但功能强大的配置功能，Spring Boot一样支持

在Spring Boot中，你会发现你引入的所有包都是*starter*形式，如：

-  `spring-boot-starter-web-services`，针对SOAP Web Services
-  `spring-boot-starter-web`，针对Web应用与网络接口
-  `spring-boot-starter-jdbc`，针对JDBC
-  `spring-boot-starter-data-jpa`，基于hibernate的持久层框架
-  `spring-boot-starter-cache`，针对缓存支持
- 等等

Spring Boot对starter的解释如下：

> Starters are a set of convenient dependency descriptors that you can include in your application. You get a one-stop-shop for all the Spring and related technology that you need, without having to hunt through sample code and copy paste loads of dependency descriptors. For example, if you want to get started using Spring and JPA for database access, just include the spring-boot-starter-data-jpa dependency in your project, and you are good to go

这句话的译意为：

> Starters是一系列极其方便的依赖描述，通过在你的项目中包含这些starter，你可以一站式获得你所需要的服务，而无需像以往那样copy各种示例配置及代码，然后调试，真正做到开箱即用；比如你想使用Spring JPA进行数据操作，只需要在你的项目依赖中引入spring-boot-starter-data-jpa即可

# Spring，Spring MVC，Spring Boot 三者比较

其实写到这里，很多读者应该已经清楚，这三者专注的领域不同，解决的问题也不一样；总的来说，Spring 就像一个大家族，有众多衍生产品例如 Boot，Security，JPA等等。但他们的基础都是Spring 的 IOC 和 AOP，IOC提供了依赖注入的容器，而AOP解决了面向切面的编程，然后在此两者的基础上实现了其他衍生产品的高级功能；Spring MVC是基于 Servlet 的一个 MVC 框架，主要解决 WEB 开发的问题，因为 Spring 的配置非常复杂，各种xml，properties处理起来比较繁琐。于是为了简化开发者的使用，Spring社区创造性地推出了Spring Boot，它遵循约定优于配置，极大降低了Spring使用门槛，但又不失Spring原本灵活强大的功能，下面用一张图来描述三者的关系：





![img](https:////upload-images.jianshu.io/upload_images/4185175-a0a50bf022178e1d.png)



最后一句话总结：**Spring MVC和Spring Boot都属于Spring，Spring MVC 是基于Spring的一个 MVC 框架，而Spring Boot 是基于Spring的一套快速开发整合包**