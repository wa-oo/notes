## 依赖注入

```
mvn -Pnexus dependency:tree   	查看依赖关系
mvn -Pnexus dependency:resolve	解决依赖关系，根据POM文件，下载或者更新该项目所依赖的库文件。
mvn -Pnexus dependency:sources	下载依赖关系的源码
```

## Bean概述

##### 在bean定义外给bean起别名

```java
<alias name="fromName" alias="toName"/>
```

##### 实例化bean

一个bean的定义本质上就是创建一个或者多个对象的食谱,容器查看这个食谱并使用被bean定义封装的配置元数据来创建(或获取)实际的对象  

1. 使用构造方法实例化

   ```xml
   <bean id="exampleBean" class="examples.ExampleBean"/>	必须提供默认的构造方法
   ```

2. 使用静态工厂方法实例化

   当使用静态工厂方法创建一个bean时,需要使用class属性指定那个包含静态工厂的类,并使用factory-method属性指定工厂方法的名字

   静态工厂用于生成实例化对象,所有的方法必须是static

   ```xml
   <bean id="clientService" class="examples.ClientService" factory-method="creatInstance"/>
   	class 确定静态工厂全限定类名
   	factory-method 确定静态方法名
   ```

   ```java
   public class ClientService{
       private static ClientService clientService = new ClientService();
       private ClientService() {}
       
       public static ClientService createInstance(){
           return clientService;
       }
   }
   ```

3. 使用实例的工厂方法实例化(非静态)

   与使用静态工厂方法实例化类似,使用实例的工厂方法实例化是调用一个已存在的bean的非静态方法来创建一个新的bean,也就是说必须现有工厂实例对象,通过实例对象创建对象,提供的方法必须都不是静态的

   ```xml
   <bean id="serviceLocator" class="examples.DefaultServiceLocator"></bean>
   <bean id="clientService" factory-method="serviceLocator" factory-method="createClientServiceInstance"></bean>
   ```

   ```java
   public class DefaultServiceLocator{
       private static ClientService clientService = new ClientServieImpl();
       private DefaultServiceLocator(){}
       
       public ClientService createClientServiceInstance(){
           return clientService;
       }
   }
   ```


##### 作用域

用于确定spring创建bean实例个数	scope

1. singleton

   在spring IOC容器中仅存在一个bean实例，bean以单例方式存在,默认值

2. prototype

   每次从容器中调用bean时,都返回一个新实例,即每次调用getBean()时,相当于执行new XXXBean(); 

3. request

   每次HTTP请求都会创建一个新的bean,该作用域仅适用于WebApplicationContext环境

4. session

   同一个HTTP Session共享一个Bean,不同session使用不同的bean,仅适用于WebApplicationContext环境

5. globalSession

   一般用于Portlet应用环境,该作用域仅适用于WebApplicationContext环境

#### 注解装配Bean

```java
1.	@Component				取代<bean class="">
	@Component("id")		取代<bean id="" class="">
2.web开发,提供三个注解取代<bean class="">
	@Repository				dao层
	@Service				service层
	@Controller				web层
3.依赖注入
	@Value("")				普通值
	@Autowried				按照类型注入引用值
	@Autowried
	@Qualifier("名称")		按照名称注入引用值
	@Resource("名称")			按照名称注入引用值
4.生命周期
	初始化:@PostConstruct
	销毁:	@PreDestroy
5.作用域
	@Scope("prototype")		多例
```

##### 组件扫描

```xml
<context:component-scan base-package="包名"></context:component-scan>
```

