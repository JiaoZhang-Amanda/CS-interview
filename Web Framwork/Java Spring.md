## Spring 体系结构
![](https://atts.w3cschool.cn/attachments/image/wk/wkspring/arch1.png)
### 核心容器
包含spring-core，spring-beans，spring-context，spring-context-support和spring-expression（SpEL，Spring表达式语言，Spring Expression Language）等模块
* **spring-core**模块提供了框架的基本组成部分，包括 IoC 和依赖注入功能。
* **spring-beans** 模块提供BeanFactory，工厂模式的微妙实现，它移除了编码式单例的需要，并且可以把配置和依赖从实际编码逻辑中解耦。
* **context**模块建立在由core和beans模块的基础上建立起来的，它以一种类似于JNDI注册的方式访问对象。Context模块继承自Bean模块，并且添加了国际化（比如，使用资源束）、事件传播、资源加载和透明地创建上下文（比如，通过Servelet容器）等功能。Context模块也支持Java EE的功能，比如EJB、JMX和远程调用等。ApplicationContext接口是Context模块的焦点。spring-context-support提供了对第三方库集成到Spring上下文的支持，比如缓存（EhCache, Guava, JCache）、邮件（JavaMail）、调度（CommonJ, Quartz）、模板引擎（FreeMarker, JasperReports, Velocity）等。
* **spring-expression**模块提供了强大的表达式语言，用于在运行时查询和操作对象图。它是JSP2.1规范中定义的统一表达式语言的扩展，支持set和get属性值、属性赋值、方法调用、访问数组集合及索引的内容、逻辑算术运算、命名变量、通过名字从Spring IoC容器检索对象，还支持列表的投影、选择以及聚合等。
<br>依赖关系：
![](https://atts.w3cschool.cn/attachments/image/20181023/1540290875453691.png)
### 数据访问/集成
包括JDBC，ORM，OXM，JMS和事务处理模块
<br>JDBC=Java Data Base Connectivity，ORM=Object Relational Mapping，OXM=Object XML Mapping，JMS=Java Message Service
* **JDBC**提供JDBC抽象层，它消除了冗长的JDBC编码和对数据库供应商特定错误代码的解析。
* **ORM**提供了对流行的对象关系映射API的集成，包括JPA，JDO和Hibernate等。通过此模块可以让ORM框架和Spring的其他功能整合，比如事务管理。
* **OXM**提供对OXM实现的支持，比如JAXB，Castor，XML Beans，JiBX，XStream等
* **JMS**包含生产和消费等功能
* **事务**实现特殊接口类及所有的POJO支持编程式和声明式事务管理。
### Web
包含Web，Web-MVC，Web-Socket和Web-Portlet
* **Web**提供面向Web的基本功能和面向web的应用上下文，比如多部分文件上传功能使用Servlet监听器初始化loC容器等。包括HTTP客户端以及Spring远程调用中与web相关的部分
* **Web-MVC**为web应用提供了模型试图控制（MVC）和REST Web服务的实现。Spring的MVC框架可以使领域模型代码和web表单完全地分离，且可以与Spring框架的其它所有功能进行集成。
* **Web-Socket**模块为 WebSocket-based 提供了支持，而且在 web 应用程序中提供了客户端和服务器端之间通信的两种方式。
* **Web-Portlet**模块提供了用于Portlet环境的MVC实现，并反映了spring-webmvc模块的功能。
### 其他
包含AOP，Aspects，Instrumentation，Web和测试模块
* **AOP**模块提供了面向方面的编程实现，允许你定义方法拦截器和切入点对代码进行干净地解耦，从而使实现功能的代码彻底的解耦出来。使用源码级的元数据，可以用类似于.Net属性的方式合并行为信息到代码中。
* **Aspects**模块提供了与 AspectJ 的集成，这是一个功能强大且成熟的面向切面编程（AOP）框架。
* **Instrumentation**模块在一定的应用服务器中提供了类 instrumentation 的支持和类加载器的实现。
* **Messaging**为 STOMP 提供了支持作为在应用程序中 WebSocket 子协议的使用。它也支持一个注解编程模型，它是为了选路和处理来自 WebSocket 客户端的 STOMP 信息。
* **测试**模块支持对具有 JUnit 或 TestNG 框架的 Spring 组件的测试。
