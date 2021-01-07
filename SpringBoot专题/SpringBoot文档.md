<h2>SpringBoot</h2>

<h3>SpringBoot简介</h3>

	1.SpringBoot是Spring家族中的一个全新的框架，它用来简化Spring应用程序的创建和开发过程，也可以说SpringBoot能简化我们之前采用的SpringMVC+Spring+MyBatis框架进行开发的过程。
	
	2.在以往我们采用SpringMVC+Spring+MyBatis框架进行开发的时候、搭建和整合三大框架，我们需要做很多工作，比如配置web.xml，配置Spring，配置MyBatis，并将它们整合在一起等，而SpringBoot框架对此开发过程进行了革命的颠覆，抛弃了繁琐的xml配置过程，采用大量的默认配置简化我们的开发过程。
	
	3.所以采用SpringBoot可以非常容易和快速的创建基于Spring框架的应用程序，他让编码变简单了，配置变简单了，部署变简单了，监控变简单了。
	
	4.正因为Springboot它化繁为简，让开发变得极其简单和快速，所以在业界备受关注。

<h3>SpringBoot的特性</h3>

	1.能够快速创建基于Spring的应用程序。
	
	2.能够直接使用java main方法启动内嵌的Tomcat、Jetty服务器运行SpringBoot程序，不需要部署war包文件。
	
	3.提供约定的starter POM 来简化Maven配置，让Maven的配置变得简单。
	
	4.根据项目的Maven依赖配置，SpringBoot自动配置Spring、SpringMVC等。
	
	5.提供了程序的健康检查功能。
	
	6.基本可以完全不使用XML配置文件，采用注解配置。

<h3>SpringBoot四大核心</h3>

	1.自动配置：针对很多Spring应用程序和常见的应用功能，SpringBoot能自动提供相关配置。
	
	2.起步依赖：告诉SpringBoot需要什么功能，它就能引入需要的依赖库。
	
	3.Actuator：让你能够深入运行中的SpringBoot应用程序，一探SpringBoot程序的内部信息。
	
	4.命令行界面：这是SpringBoot的可选特性，主要针对Groovy语言使用。

<h3>SpringBoot开发环境</h3>

	1.推荐使用SpringBoot最新版本，目前SpringBoot的最新正式版为1.5.9.RELEASE;
	
	2.如果使用eclipse，推荐安装Spring Tool Suite(STS)插件；
	
	3.如果使用IDEA旗舰版，自带了SpringBoot插件；
	
	4.推荐使用Maven3.0+,Maven目前最新版本为3.5.2;
	
	5.推荐使用Java8，虽然SpringBoot也兼容Java6;

<h3>第一个SpringBoot程序</h3>

	快速开发一个SpringBoot程序步骤如下：
	
		1.创建一个SpringBoot项目;
	
			可以采用方式一:使用eclipse的Spring Tool Suite(STS)插件/或者IDEA自带的插件创建;
	
			可以采用方式二:直接使用Maven创建项目的方式创建;
	
		2.加入SpringBoot的父级和起步依赖；
	
		3.创建SpringBoot的入口main方法；
	
		4.创建一个SpringMVC的Controller；
	
		5.运行SpringBoot的入口main方法；
	
		至此，第一个SpringBoot程序开发完成。

<h3>第一个SpringBoot程序解析</h3>

	1.SpringBoot的父级依赖spring-boot-starter-parent配置之后，当前的项目就是SpringBoot项目。
	
	2.spring-boot-starter-parent是一个特殊的starter依赖，它用来提供相关的Maven默认依赖，使用它之后，常用的jar包依赖可以省去version配置。
	
	3.SpringBoot提供了哪些默认jar包的依赖，可查看该父级依赖的pom文件。
	
	4.如果不想使用某个默认的依赖版本，可以通过pom.xml文件的属性配置覆盖各个依赖项，比如覆盖Spring版本。
	
	5.@SpringBootApplication注解是SpringBoot项目的核心注解，主要作用是开启Spring自动配置。
	
	6.main方法是一个标准的Java程序的main方法，主要作用是作为项目运行的入口。
	
	7.@Controller及@ResponseBody依然是我们之前的SpringMVC,因为SpringBoot的里面依然使用我们的SpringMVC + Spring + MyBatis等框架。

<h3>SpringBoot的核心配置文件</h3>

	SpringBoot的核心配置文件用于配置SpringBoot程序，有两种格式的配置文件:
	
		1.properties文件
	
			键值对的properties属性文件配置方式
	
		2.yml文件
	
			yml是一种yaml格式的配置文件，主要采用一定的空格，换行等格式排版进行配置。
	
			yaml是一种直观的能够被计算机识别的数据序列化格式，容易被人类阅读，yaml类似于xml,
	
			但是语法比xml简洁很多。
	
			值与前面的冒号配置项必须要有一个空格.
	
			yml后缀也可以使用yaml后缀。
	
		配置示例:
	
			<font color="red">(一)properties文件配置方式</font>			

```properties
			#配置服务器端口
			server.port=9800
			#配置应用访问路径
			server.context-path=/13-springboot-web
```

			<font color="red">(二)yml文件配置方式		</font>

```yml
			server:
				port: 9800
				context-path: /13-springboot-web
```

		多环境配置文件

```properties
		#比如配置测试环境

			spring.profiles.active=dev

			application-dev.properties

		#比如配置生产环境

			spring.profiles.active=product

			application-product.properties	
```

		

```yml
#配置tomcat的启动端口号
#server:
  #port: 8080
#配置应用程序的上下文路径
  #context-path: /springBoot-demo


#模拟不同开发环境下的配置文件
#激活配置文件，如果激活的配置文件中的内容与本配置文件中的内容一致，激活的配置文件内容会覆盖掉本配置文件中的内容
spring:
  profiles:
    #激活application-online.yml(项目上线环境)
    #active: online
    #激活application-test.yml(项目测试环境)
    #active: test
    #激活application-dev.yml(项目开发环境)
    active: dev
```

<h3>SpringBoot自定义配置</h3>

	我们可以在SpringBoot的核心配置中自定义配置，然后采用如下注解读取配置的属性值
	
		1、@Value注解(Spring框架提供的注解)
	
			写法：			

```java
			@Value("${node.name}")
			private String name;
```

		2、@ConfigurationProperties
	
			用于将整个文件映射成一个对象，比如:		

```java
			@Component
			@ConfigurationProperties(prefix="node")
			public class MyConfig{
				private String name;
				private String location;

				public String getName(){
					return name;
				}

				public void setName(String name){
					this.name = name;
				}

			}
```

<h3>SpringBoot下的SpringMVC</h3>

	SpringBoot下的SpringMVC和之前的SpringMVC使用是完全一样的:
	
		@Controller
	
			即为SpringMVC注解，处理http请求;
	
		@RestController
	
			Spring4后新增注解;
	
			是@Controller与@ResponseBody的组合注解;
	
			用于返回字符串或json数据;
	
		@GetMapping
	
			@RequestMapping和Get请求方法的组合;
	
			等价于@RequestMapping(value = "/user",method = RequestMethod.GET)
	
		@PostMapping
	
			@RequestMapping和Post请求方法的组合;
	
			等价于@RequestMapping(value = "/user",method = RequestMethod.POST)
	
		@PutMapping
	
			@RequestMapping和PUT请求方法的组合;
	
			等价于@RequestMapping(value = "/user",method = RequestMethod.PUT)
	
		@DeleteMapping
	
			@RequestMapping和Delete请求方法的组合
	
			等价于@RequestMapping(value = "/user",method = ReuqestMethod.DELETE)

```java
//@Controller
/**
 *	@RestController = @Controller + @ResponseBody,用于返回字符串或者是json数据
 */
@RestController
public class ConfigInfoController {

    /*@Value("${provider.name}")
    private String name;

    @Value("${provider.location}")
    private String location;*/

    @Resource
    private MyConfig myConfig;      //注入配置类

    @RequestMapping(value = "/configinfo")
    public String configInfo(){
        return "姓名为:"+ myConfig.getName() + ",位置为:" + myConfig.getLocation();
    }
	/**
	 *	//只能以get请求方式进行访问
	 */
    @RequestMapping(value = "/user1",method = RequestMethod.GET)     
    public User getUser(){
        User user = new User();
        user.setName("徐唯国");
        user.setPassword("12345678");
        user.setAge(12);
        return user;
    }

    /**
     * GetMapping等价于@RequestMapping(value = "/user1",method = RequestMethod.GET)
     * @return
     */
    @GetMapping(value = "/user")
    public User getUser1(){
        User user = new User();
        user.setAge(19);
        user.setName("张三");
        user.setPassword("zhangsan123");
        return user;
    }

    /**
     * PostMapping等价于@RequestMapping(value = "/user2",method = RequestMethod.POST)
     * @return
     */
    @PostMapping(value = "/user")
    public User getUser2(){
        User user = new User();
        user.setAge(19);
        user.setName("李四");
        user.setPassword("lisi123");
        return user;
    }

    /**
     * PutMapping等价于@RequestMapping(value = "/user3",method = ReuqestMethod.PUT)
     * @return
     */
    @PutMapping(value = "/user")
    public User getUser3(){
        User user = new User();
        user.setAge(19);
        user.setName("小红");
        user.setPassword("xiaohong123");
        return user;
    }

    /**
     * DeleteMapping等价于@RequestMapping(value = "/user4",method = RequestMethod.DELETE)
     * @return
     */
    @DeleteMapping(value = "/user")
    public User getUser4(){
        User user = new User();
        user.setAge(19);
        user.setName("小王");
        user.setPassword("xiaowang123");
        return user;
    }
}
```

<h3>SpringBoot使用JSP</h3>

	在SpringBoot中使用jsp，按如下步骤进行:
	
		1、在pom.xml文件中配置依赖项:

```xml
        <!--引入SpringBoot内嵌的Tomcat对JSP的解析包-->
        <dependency>
           <groupId>org.apache.tomcat.embed</groupId>
           <artifactId>tomcat-embed-jasper</artifactId>
        </dependency>

        <!--servlet依赖的jar包-->
        <dependency>
           <groupId>javax.servlet</groupId>
           <artifactId>javax.servlet-api</artifactId>
        </dependency>

        <!--jsp依赖jar包-->
        <dependency>
           <groupId>javax.servlet.jsp</groupId>
           <artifactId>javax.servlet.jsp-api</artifactId>
           <version>2.3.1</version>
        </dependency>

        <!--jstl标签依赖的jar包-->
        <dependency>
           <groupId>javax.servlet</groupId>
           <artifactId>jstl</artifactId>
        </dependency>
```

		2、在application.properties文件配置spring mvc的视图展示为jsp(相当于之前在springmvc-		servlet.xml中配置的视图解析器):

```properties
		spring.mvc.view.prefix = /
		spring.mvc.view.suffix = .jsp
```

		3、在src/main下创建一个webapp目录，然后再该目录下新建jsp页面
	
		build中要配置备注中的配置信息		

```xml
        <!--因为idea默认不会编译main包以及子包下的配置文件，所以需要手动指定-->
        <resources>
           <resource>
              <directory>src/main/java</directory>
              <includes>
                 <include>**/*.xml</include>
              </includes>
           </resource>

           <resource>
              <directory>src/main/resources</directory>
              <includes>
                 <include>**/*.*</include>
              </includes>
           </resource>

           <resource>
              <directory>src/main/webapp</directory>
              <!--将jsp文件编译到指定的路径-->
              <targetPath>META-INF/resources</targetPath>
              <includes>
                 <include>**/*.*</include>
              </includes>
           </resource>
        </resources>
```

<h3>SpringBoot集成MyBatis的步骤如下</h3>

	1、在pom.xml中配置相关jar依赖	

```xml
    <!--SpringBoot整合MyBatis所需要用到的jar包-->
    <dependency>
       <groupId>org.mybatis.spring.boot</groupId>
       <artifactId>mybatis-spring-boot-starter</artifactId>
       <version>1.3.1</version>
    </dependency>

    <!--MySQL的驱动包-->
    <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
    </dependency>
```

	2、在SpringBoot的核心配置文件application.properties/yml中配置MyBatis的Mapper.xml文件所在位置:

```yml
	mybatis:
		mapper-locations: classpath:com.github.springboot.mapper.*.xml
```

	3.在SpringBoot的核心配置文件application.properties/yml中配置数据源:

```yml
	spring:
		datasource:
			driver-class-name: com.mysql.jdbc.Driver
			url: jdbc:mysql://localhost:3306/smbms?	    useUnicode=true&characterEncoding=utf8
			username: root
			password: 123
```

	4.在MyBatis的Mapper接口中添加@Mapper注解 或者在运行的主类上添加@MapperScan("com.github.mapper")注解包扫描。

<h3>SpringBoot事务支持</h3>

	SpringBoot使用事务非常简单:
	
		1、在入口类中使用注解@EnableTransactionManagement开启事务支持;
	
		2、在访问数据库的service方法上添加注解@Transactional即可;
<h3>SpringBoot实现RESTfull API</h3>

	认识RESTfull
	
		什么是RESTfull?
	
			RESTfull是一种互联网架构设计风格，但它并不是标准，它只是提出了一组客户端和服务器交互时的架构理念和设计原则，基于这种理念和原则设计的接口可以更简洁，更有层次;
	
			任何的技术都可以实现这种理念。
	
			REST这个词，是Roy Thomas Fielding在他2000年的博士论文中提出的;
	
			如果一个架构符合REST原则，就称他为RESTfull架构;
	
			比如我们要访问一个http接口: http://localhost:8080/api/order?id=12&starus=1
	
			采用RESTfull风格则http地址为: http://localhost:8080/api/order/1202/1
	
	SpringBoot开发RESTfull
	
		SpringBoot开发RESTfull主要是几个注解实现
	
			1、@PathVariable
	
				获取url中的数据;
	
				该注解是实现RESTfull最主要的一个注解;
	
			2、增加post方法
	
			3、删除delete方法
	
			4、修改put方法
	
			5、查询get方法

<h3>SpringBoot热部署插件</h3>

	在实际开发中，我们修改某些代码逻辑功能或页面都需要重启应用，这无形中降低了开发效率；
	
	热部署是指当我们修改代码后，服务能自动加载新修改的内容，这样大大提高了我们开发的效率；
	
	SpringBoot热部署通过添加一个插件实现:
	
		插件为:spring-boot-devtools,在Maven中配置如下:

```xml
        <!--springBoot 开发自动热部署-->
        <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-devtools</artifactId>
           <optional>true</optional>
        </dependency>
```

	该热部署插件在实际应用中会有一些小问题，明明已经重启，但没有生效，这种情况下，手动重启一下程序;

<h3>SpringBoot集成Redis</h3>

	SpringBoot集成Redis的步骤如下:
	
		1、在pom.xml中配置相关的依赖

```xml
        <!--加载SpringBoot redis包-->
        <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-data-redis</artifactId>
        </dependency>
```

		2、在SpringBoot核心配置文件application.properties/yml中配置redis连接信息:				

```yml
		spring:
			redis:
				host: 192.168.160.128
				port: 6379
				password: 123456
```

		3、配置了上面的步骤，SpringBoot将自动配置RedisTemplate，在需要操作的redis类中注入redisTemplate;
	
		在使用的类中注入:		

```java
		@Autowired
		private RedisTemplate<String,String> redisTemplate;

		@Autowired
		private RedisTemplate<Object,Object> redisTemplate;
```

		SpringBoot帮我们注入的redisTemplate类，泛型里面只能写<String,String>、<Object,Object>


<h3>SpringBoot集成Dubbo</h3>

	集成前的准备
	
		1、阿里巴巴提供的dubbo集成SpringBoot开源项目;
	
		https://github.com/alibaba
	
		2、我们采用该项目提供的jar包进行集成;	

```xml
        <!--springboot集成dubbo的起步依赖(阿里巴巴提供)-->
        <dependency>
           <groupId>com.alibaba.spring.boot</groupId>
           <artifactId>dubbo-spring-boot-starter</artifactId>
           <version>1.0.0</version>
        </dependency>
```

	正式集成	
	
		开发Dubbo服务接口
	
		开发Dubbo服务提供者
	
			1、创建一个SpringBoot项目并配置好相关的依赖;
	
			2、加入SpringBoot与Dubbo集成的起步依赖:

```xml
			 <!--springboot集成dubbo的起步依赖(阿里巴巴提供)-->
            <dependency>
               <groupId>com.alibaba.spring.boot</groupId>
               <artifactId>dubbo-spring-boot-starter</artifactId>
               <version>1.0.0</version>
            </dependency>
```
			3、在SpringBoot的核心配置文件application.properties/yml中配置dubbo的信息:			

```yml
            #Web服务端口
            server:
                port: 8080

            #Dubbo配置
            spring:
                dubbo:
                    appname: springboot-dubbo-provider
                    registry: zookeeper://192.168.160.128:2181
```

				由于使用了zookeeper作为注册中心，则需要加入zookeeper的客户端jar包:				

```xml
                <!--既然使用了zookeeper作为注册中心，所以需要导入zookeeper客户端驱动依赖-->
                <dependency>
                   <groupId>com.101tec</groupId>
                   <artifactId>zkclient</artifactId>
                   <version>0.10</version>
                </dependency>
```

			4、编写Dubbo的接口实现类:

```java
        /**
         * 该类实现服务接口UserService中的所有方法
         */
        @Service(interfaceClass = UserService.class)  //该注解为Dubbo提供的注解，属性interfaceClass为你要实现的服务接口的class文件
        @Component      //标记为组件类
        public class UserServiceImpl implements UserService {

            @Resource
            private UserMapper userMapper;

            @Override
            public String sayHello(String s) {
                if (s != null){
                    return "Hello SpringBoot" + s + "!";
                }
                return "Hello Dubbo!";
            }

            @Override
            public List<ItripUser> getItripUserList() {
                return userMapper.getItripUserList();
            }
        }
```

			5、编写一个入口main程序启动Dubbo服务消费者:			

```java
        @SpringBootApplication
        @EnableDubboConfiguration     //启用可用的Dubbo配置
        public class DubboProviderApplication {

           public static void main(String[] args) {
              SpringApplication.run(DubboProviderApplication.class, args);
           }

        }
```

	开发Dubbo服务消费者	
	
		1、创建一个SpringBoot项目并配置好相关的依赖;
	
		2、加入SpringBoot与Dubbo集成的起步依赖:

```xml
		 <!--springboot集成dubbo的起步依赖(阿里巴巴提供)-->
        <dependency>
           <groupId>com.alibaba.spring.boot</groupId>
           <artifactId>dubbo-spring-boot-starter</artifactId>
           <version>1.0.0</version>
        </dependency>
```
		3、在SpringBoot的核心配置文件application.properties/yml中配置dubbo的信息:		

```yml
		#Web服务端口
		server:
			port: 9092
			
		spring:
			dubbo:
				appname: dubbo-consumer
				registry: zookeeper://192.168.160.128:2181
```

		由于使用了zookeeper作为注册中心，则需要加入zookeeper的客户端jar包:	

```xml
   				<!--既然使用了zookeeper作为注册中心，所以需要导入zookeeper客户端驱动依赖-->
                <dependency>
                   <groupId>com.101tec</groupId>
                   <artifactId>zkclient</artifactId>
                   <version>0.10</version>
                </dependency>
```

		4、编写一个Controller类，调用远程的Dubbo服务。			

```java
        @RestController
        public class UserController {

            @Reference //此注解的作用是注入分布式中的远程服务对象
            private UserService userService;

            @RequestMapping(value = "/dubbo/sayHello",
                            method = RequestMethod.GET,
                            produces = "application/json")
            public String sayHello(String s){
                return userService.sayHello(s);
            }

            @RequestMapping(value = "/dubbo/itripUser",
                            method = RequestMethod.GET,
                            produces = "application/json")
            public List<ItripUser> getItripUserList(){
                List<ItripUser> itripUserList = userService.getItripUserList();
                if (itripUserList != null){
                    return itripUserList;
                }
                return null;
            }

}
```

		5、编写一个入口main程序启动Dubbo消费者。			

```java
		@SpringBootApplication
		@EnableDubboConfiguration  //引用可用的dubbo配置
		public class DubboConsumerApplication {

   			public static void main(String[] args) {
     		 SpringApplication.run(DubboConsumerApplication.class, args);
   			}

		}
```

<h3>SpringBoot使用拦截器</h3>

	1、按照SpringMVC的方式编写一个拦截器类;	

```java
    /**
     * 登录拦截器
     */
    public class LoginInterceptor implements HandlerInterceptor {

        /**
         * 如果该方法的返回值为true，则进入Controller，否则，不进入Controller
         * @param httpServletRequest
         * @param httpServletResponse
         * @param o
         * @return
         * @throws Exception
         */
        @Override
        public boolean preHandle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o) throws Exception {
            System.out.println("已经进入了登录拦截器!");
            return true;
        }

        @Override
        public void postHandle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, ModelAndView modelAndView) throws Exception {

        }

        @Override
        public void afterCompletion(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, Exception e) throws Exception {

        }
    }
```

	2、编写一个配置类继承WebMvcConfigurerAdapter类		

```java
    @Configuration      //变为配置类
    public class WebConfig extends WebMvcConfigurerAdapter {

        /**
         * 添加拦截器
         * @param registry
         */
        @Override
        public void addInterceptors(InterceptorRegistry registry) {

            //定义要拦截的路径数组
            String [] addPathPatterns = {"/boot/**","/user"};

            //定义不拦截的路径数组
            String [] excludePathPatterns = {"/itripUser","/updateUser/{userName}"};

            //注册拦截器
            InterceptorRegistration interceptor = registry.addInterceptor(new LoginInterceptor());
            //指定好要拦截的路径,参数为字符串(可变参数)
            interceptor.addPathPatterns(addPathPatterns);
            //指定好不拦截的路径,参数为字符串(可变参数)
            interceptor.excludePathPatterns(excludePathPatterns);

        }
    }
```

	3、为该配置添加@Configuration注解，标注此类为一个配置类，让SpringBoot扫描到;
	
	4、覆盖其中的方法并添加已经配置好的拦截器:

<h3>SpringBoot使用Servlet</h3>

	方式一:
	
		通过注解的方式实现:
	
			1、使用Servlet3的注解方式编写一个Servlet		

```java
        /**
         * SpringBoot整合Servlet
         */
        @WebServlet(urlPatterns = "/myServlet")
        public class MyServlet extends HttpServlet {

            private static final long servletId = -323211321321312323L;

            @Override
            protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
                response.getWriter().print("我的Servlet,HelloWorld");
                response.getWriter().flush();
                response.getWriter().close();
            }

            @Override
            protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
                super.doPost(request, response);
            }
        }
```

			2、在main方法的主类上添加注解:@ServletComponentScan(basePackages = "com.github.servlet")
	
	方式二:
	
		通过SpringBoot的配置类实现:
	
			1、编写一个普通的Servlet

```java
            public class HeServlet extends HttpServlet {
                @Override
                protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
                    resp.getWriter().print("He Servlet Hello World!");
                    resp.getWriter().flush();
                    resp.getWriter().close();
                }

                @Override
                protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
                    super.doPost(req, resp);
                }
            }
```

			2、编写一个SpringBoot的配置类

```java
            /**
             * springboot没有xml配置文件，类名上方添加@Configuration注解可以表示这个类是一个spring的配置文件
             */
            @Configuration
            public class ServletConfig {
                /**
                 * @Bean注解等价于<bean id="servletRegistrationBean" class="HeServlet的全路径名"></bean>
                 * @return
                 */
                @Bean
                public ServletRegistrationBean servletRegistrationBean(){
                    ServletRegistrationBean registrationBean = new ServletRegistrationBean(new HeServlet(), "/heServlet");
                    return registrationBean;
                }
            }
```

<h3>SpringBoot实现Filter</h3>

	方式一
	
		通过注解的方式实现;
	
			1、编写一个Servlet3的注解过滤器				

```java
@WebFilter(urlPatterns = "/myFilter")
public class MyFilter implements Filter {
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("进入了初始化方法");
    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("您已经进入filter过滤器，一切请求正常");
        filterChain.doFilter(servletRequest,servletResponse);
    }

    @Override
    public void destroy() {

    }
}
```

			2、在main方法的主类上添加注解:@ServletComponentScan(basePackages = {"com.github.servlet","com.github.filter"})		
	
	方式二
	
		通过springboot的配置类方式实现;
	
		1、编写一个普通的过滤器类			

```java
        public class HeFilter implements Filter {
            @Override
            public void init(FilterConfig filterConfig) throws ServletException {
                System.out.println("进入HeFilter初始化方法");
            }

            @Override
            public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
                System.out.println("进入HeFilter方法，一切请求执行正常");
            }

            @Override
            public void destroy() {

            }
        }
```

		2、编写一个SpringBoot的配置类				

```java
/**
 * springboot没有xml配置文件，类名上方添加@Configuration注解可以表示这个类是一个spring的配置文件
 */
@Configuration
public class ServletConfig {
    /**
     * @Bean注解等价于<bean id="servletRegistrationBean" class="HeServlet的全路径名"></bean>
     * @return
     */
    @Bean
    public ServletRegistrationBean servletRegistrationBean(){
        //将Servlet注入到Bean中
        ServletRegistrationBean registrationBean = new ServletRegistrationBean(new HeServlet(), "/heServlet");
        return registrationBean;
    }

    /**
     * 等价于<bean id="filterRegistrationBean" class="HeFilter的全路径名"></bean>
     * @return
     */
    @Bean
    public FilterRegistrationBean filterRegistrationBean(){
        //将Filter注入到bean中
        FilterRegistrationBean registrationBean = new FilterRegistrationBean(new HeFilter());
        //添加filter拦截url
        registrationBean.addUrlPatterns("/heFilter");
        return registrationBean;
    }
}
```

<h3>SpringBoot项目配置字符编码</h3>

	1、第一种方式是使用传统Spring提供给的字符编码过滤器

```java
/**
 * 解决请求中文乱码问题，等价于web.xml中的:
 * <filter>
 *     <filter name = "characterEncodingFilter"></filter>
 *     <filter class = "CharacterEncodingFilter的全类名"></filter>
 * </filter>
 *
 * <filter-mapping>
 *     <filter name = "characterEncodingFilter"></filter>
 *     <init-param>
 *         <param-name>encoding</param-name>
 *         <param-value>UTF-8</param-value>
 *     </init-param>
 *     <url-prettern>/*</url-prettern>
 * </filter-mapping>
 * @return
 */
@Bean
public FilterRegistrationBean filterRegistrationBean(){
    FilterRegistrationBean registrationBean = new FilterRegistrationBean();
    //设置原先在web.xml中配置的字符编码过滤器
    CharacterEncodingFilter characterEncodingFilter = new CharacterEncodingFilter();
    characterEncodingFilter.setForceEncoding(true);
    characterEncodingFilter.setEncoding("UTF-8");
    registrationBean.setFilter(characterEncodingFilter);
    //设置过滤器拦截的路径
    registrationBean.addUrlPatterns("/*");
    return registrationBean;

}
```

		在主类上需要扫描过滤器，扫描包或者class:basePagkages = 	org.springframework.web.filter.CharacterEncodingFilter.class
	
		注意：只有当spring.http.encoding.enabled = false配置成false后，过滤器才会起作用;
	
	2、第二种方式是在application.properties/yml中配置字符编码;
	
		从springboot1.4.2之后开始新增的一种字符编码设置;

```yml
		spring:
			http:
				encoding:
					charset: UTF-8
					enabled: true
					force: true
```

<h3>SpringBoot访问静态资源文件(js、css、html)</h3>

	1.引入SpringBoot访问静态文件的jar依赖

```xml
    <!--引用SpringBoot加载静态文件的jar依赖-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
```

	2.将静态资源文件放在resources包下，css文件、js文件、img文件放在static文件夹下，html文件放在templates文件夹下。
	在springboot 中，templates中的文件是需要通过视图解析器才能去方问的。