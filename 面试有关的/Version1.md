### **说说对springmvc的理解**

1. ### 什么是Spring MVC ？简单介绍下你对springMVC的理解?

  Spring MVC是一个基于Java的实现了MVC设计模式的轻量级Web框架，通过把Model，View，Controller分离，将web层进行职责解耦，把复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。

2. ### SpringMVC的流程？

2. ![img](https://img-blog.csdnimg.cn/106b2308120242689ee2c246093d23c5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBASFJYOTg=,size_20,color_FFFFFF,t_70,g_se,x_16)


3. ### Springmvc的优点

  可以支持各种视图技术，而不仅仅局限于JSP；
  与Spring框架集成（如IoC容器、AOP等）；
  清晰的角色分配：前端控制器(dispatcherServlet) ，请求到处理器映射（handlerMapping)，处理器适配（HandlerAdapter)，视图解析器（ViewResolver）。
  支持各种请求资源的映射策略。
4. ### SpringMVC怎么样设定重定向和转发的

  转发：在返回值前面加"forward:"，譬如"forward:user.do?name=method4"
  重定向：在返回值前面加"redirect:"，譬如"redirect:http://www.baidu.com"
5. ### SpringMVC常用的注解有哪些

  @RequestMapping：用于处理请求 url 映射的注解，可用于类或方法上。用于类上，则表示类中的所有响应请求的方法都是以该地址作为父路径。
  @RequestBody：注解实现接收http请求的json数据，将json转换为java对象
  @ResponseBody：注解实现将conreoller方法返回对象转化为json对象响应给客户
6. ### SpingMvc中的控制器的注解一般用哪个？有没有别的注解可以替代？

  一般用**@Controller注解，也可以使用@RestController**，@RestController注解相当于@ResponseBody ＋ @Controller，表示是表现层，除此之外，一般不用别的注解代替。

7. ### 如何解决POST请求中文乱码问题

  解决post请求乱码问题：在web.xml中配置一个CharacterEncodingFilter过滤器，设置成utf-8

8. ### get请求中文参数出现乱码怎么解决？

  修改tomcat配置文件，添加编码与工程编码一致
  <ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
  1
  对参数进行重新编码，ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码。
  String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8")
  1
9. ### SpringMvc里面拦截器是怎么写的

  一种是实现HandlerInterceptor接口，另外一种是继承适配器类

10. ### 什么是注解

    Java 注解就是代码中的一些特殊标记
    用于在编译、类加载、运行时进行解析和使用，并执行相应的处理
    本质是继承了 Annotation 的特殊接口
    具体实现类是 JDK 动态代理生成的代理类，通过反射获取注解时，返回的也是 Java 运行时生成的动态代理对象
11. ### SpringMvc怎么和AJAX相互调用的

    通过Jackson框架就可以把Java对象直接转化成Json对象

​		加入Jackson.jar
​		配置文件中配置json的映射
​		在接收Ajax方法里面可以直接返回Object、List等，但方法前面要加上**@ResponseBody**注解

12. ### Spring MVC的异常处理

    将异常抛给Spring框架，由Spring框架来处理
    我们只需要配置简单的异常处理器，在异常处理器中添视图页面
13. ### SpringMvc的控制器是不是单例模式？如果是，有什么问题？怎么解决？

    是单例模式
    多线程访问的时候有线程安全问题
    在控制器里面不能写可变状态量，如果需要使用这些可变状态，可以使用ThreadLocal机制解决，为每个线程单独生成一份变量副本，独立操作，互不影响。
14. ### 如果在拦截请求中，我想拦截get方式提交的方法，怎么配置？

    在**@RequestMapping注解里面加上method=RequestMethod.GET**

15. ### 怎样在方法里面得到Request，或者Session

    在方法的形参中声明request，SpringMvc就自动把request对象传入

16. ### 想在拦截的方法里面得到从前台传入的参数，怎么得到？

    直接在形参里面声明这个参数就可以，但必须名字和传过来的参数一样

17. ### 前端传入多个参数，并且参数都是同个对象的，如何快速得到这个对象？

    在方法中声明这个对象，SpringMvc就自动会把属性赋值到这个对象里面

18. ### SpringMvc中函数的返回值是什么？

    可以有很多类型，有String，ModelAndView。ModelAndView类把视图和数据都合并的一起的，但一般用String比较好

19. ### SpringMvc用什么对象从后台向前台传递数据的？

    通过ModelMap对象，可以在这个对象里面调用put方法，把对象加到里面，前端就可以通过el表达式拿到。

20. ### 怎么样把ModelMap里面的数据放入Session里面？

在类上面加上@SessionAttributes注解，里面包含的字符串就是要放入session里面的key
