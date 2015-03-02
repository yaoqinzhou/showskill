###(1)Spring有哪些优点？

轻量级：Spring在大小和透明性方面绝对属于轻量级的，基础版本的Spring框架大约只有2MB。
控制反转(IOC)：Spring使用控制反转技术实现了松耦合。依赖被注入到对象，而不是创建或寻找依赖对象。
面向切面编程(AOP)：Spring支持面向切面编程，同时把应用的业务逻辑与系统的服务分离开来。
容器：Spring包含并管理应用程序对象的配置及生命周期。
MVC框架：Spring的web框架是一个设计优良的web MVC框架，很好的取代了一些web框架。
事务管理：Spring对下至本地业务上至全局业务(JAT)提供了统一的事务管理接口。
异常处理：Spring提供一个方便的API将特定技术的异常(由JDBC, Hibernate, 或JDO抛出)转化为一致的、Unchecked异常。

###(2)IOC有什么优点？

IOC或依赖注入减少了应用程序的代码量。它使得应用程序的测试很简单，因为在单元测试中不再需要单例或JNDI查找机制。
简单的实现以及较少的干扰机制使得松耦合得以实现。IOC容器支持勤性单例及延迟加载服务。

###(3)Spring中的依赖注入是什么？

依赖注入作为控制反转(IOC)的一个层面，可以有多种解释方式。在这个概念中，你不用创建对象而只需要描述如何创建它们。
你不必通过代码直接的将组件和服务连接在一起，而是通过配置文件说明哪些组件需要什么服务。之后IOC容器负责衔接。

###(4)你推荐哪种依赖注入？构造器依赖注入还是Setter方法依赖注入？

最好的选择是使用构造器参数实现强制依赖注入，使用setter方法实现可选的依赖关系。

###(5)Spring框架中单例beans是线程安全的吗？

不是，Spring框架中的单例beans不是线程安全的。

###(6)解释Spring框架中bean的生命周期

Spring容器读取XML文件中bean的定义并实例化bean。
Spring根据bean的定义设置属性值。
如果该Bean实现了BeanNameAware接口，Spring将bean的id传递给setBeanName()方法。
如果该Bean实现了BeanFactoryAware接口，Spring将beanfactory传递给setBeanFactory()方法。
如果任何bean BeanPostProcessors 和该bean相关，Spring调用postProcessBeforeInitialization()方法。
如果该Bean实现了InitializingBean接口，调用Bean中的afterPropertiesSet方法。如果bean有初始化函数声明，调用相应的初始化方法。
如果任何bean BeanPostProcessors 和该bean相关，调用postProcessAfterInitialization()方法。
如果该bean实现了DisposableBean，调用destroy()方法。

###(7)哪些是最重要的bean生命周期方法？能重写它们吗？

有两个重要的bean生命周期方法。第一个是setup方法，该方法在容器加载bean的时候被调用。
第二个是teardown方法，该方法在bean从容器中移除的时候调用。

bean标签有两个重要的属性(init-method 和 destroy-method)，你可以通过这两个属性定义自己的初始化方法和析构方法。
Spring也有相应的注解：@PostConstruct 和 @PreDestroy。

###(8)什么是Spring的内部bean？

当一个bean被用作另一个bean的属性时，这个bean可以被声明为内部bean。在基于XML的配置元数据中，
可以通过把元素定义在 或元素内部实现定义内部bean。内部bean总是匿名的并且它们的scope总是prototype。

###(9)什么是bean自动装配？

Spring容器可以自动配置相互协作beans之间的关联关系。这意味着Spring可以自动配置一个bean和其他协作bean之间的关系，
通过检查BeanFactory 的内容里没有使用和< property>元素。

###(10)解释自动装配的各种模式？

自动装配提供五种不同的模式供Spring容器用来自动装配beans之间的依赖注入:

no：默认的方式是不进行自动装配，通过手工设置ref 属性来进行装配bean。

byName：通过参数名自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byName。
之后容器试图匹配、装配和该bean的属性具有相同名字的bean。

byType：通过参数的数据类型自动自动装配，Spring容器查找beans的属性，这些beans在XML配置文件中被设置为byType。
之后容器试图匹配和装配和该bean的属性类型一样的bean。如果有多个bean符合条件，则抛出错误。

constructor：这个同byType类似，不过是应用于构造函数的参数。如果在BeanFactory中不是恰好有一个bean与构造函数参数相同类型，
则抛出一个严重的错误。

autodetect：如果有默认的构造方法，通过 construct的方式自动装配，否则使用 byType的方式自动装配。

###(11)你可以在Spring中注入null或空字符串吗？

完全可以。

###(12)@Required 注解

表明bean的属性必须在配置时设置，可以在bean的定义中明确指定也可通过自动装配设置。
如果bean的属性未设置，则抛出BeanInitializationException异常。

###(13)@Autowired 注解

注解提供更加精细的控制，包括自动装配在何处完成以及如何完成。它可以像@Required一样自动装配setter方法、
构造器、属性或者具有任意名称和/或多个参数的PN方法。

###(14)@Qualifier 注解

当有多个相同类型的bean而只有其中的一个需要自动装配时，将@Qualifier 注解和@Autowire 注解结合使用消除这种混淆，
指明需要装配的bean。

###(15)JdbcTemplate

JdbcTemplate类提供了许多方法，为我们与数据库的交互提供了便利。例如，它可以将数据库的数据转化为原生类型或对象，
执行写好的或可调用的数据库操作语句，提供自定义的数据库错误处理功能。

###(16)Spring支持的事务管理类型

编程式事务管理：这意味着你可以通过编程的方式管理事务，这种方式带来了很大的灵活性，但很难维护。

声明式事务管理：这种方式意味着你可以将事务管理和业务代码分离。你只需要通过注解或者XML配置管理事务。

###(17)Spring框架的事务管理有哪些优点？

它为不同的事务API(如JTA, JDBC, Hibernate, JPA, 和JDO)提供了统一的编程模型。
它为编程式事务管理提供了一个简单的API而非一系列复杂的事务API(如JTA).
它支持声明式事务管理。
它可以和Spring 的多种数据访问技术很好的融合。

###(18)你更推荐那种类型的事务管理？

许多Spring框架的用户选择声明式事务管理，因为这种方式和应用程序的关联较少，因此更加符合轻量级容器的概念。
声明式事务管理要优于编程式事务管理，尽管在灵活性方面它弱于编程式事务管理(这种方式允许你通过代码控制业务)。

###(19)连接点(Join point)

连接点代表应用程序中插入AOP切面的地点。它实际上是Spring AOP框架在应用程序中执行动作的地点。

###(20)通知(Advice)

通知表示在方法执行前后需要执行的动作。实际上它是Spring AOP框架在程序执行过程中触发的一些代码。

Spring切面可以执行一下五种类型的通知:

before(前置通知)：在一个方法之前执行的通知。
after(最终通知)：当某连接点退出的时候执行的通知（不论是正常返回还是异常退出）。
after-returning(后置通知)：在某连接点正常完成后执行的通知。
after-throwing(异常通知)：在方法抛出异常退出时执行的通知。
around(环绕通知)：在方法调用前后触发的通知。

###(21)切入点(Pointcut)

切入点是一个或一组连接点，通知将在这些位置执行。可以通过表达式或匹配的方式指明切入点。

###(22)什么是目标对象？

被一个或者多个切面所通知的对象。它通常是一个代理对象。也被称做被通知（advised）对象。

###(23)什么是代理？

代理是将通知应用到目标对象后创建的对象。从客户端的角度看，代理对象和目标对象是一样的。

###(24)有几种不同类型的自动代理？

BeanNameAutoProxyCreator：bean名称自动代理创建器
DefaultAdvisorAutoProxyCreator：默认通知者自动代理创建器
Metadata autoproxying：元数据自动代理

###(25)什么是织入？什么是织入应用的不同点？

织入是将切面和其他应用类型或对象连接起来创建一个通知对象的过程。织入可以在编译、加载或运行时完成。

