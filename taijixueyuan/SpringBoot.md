# SpringBoot

##### Springboot命令行

mvn -Pnexus spring-boot:run   		 	运行springboot项目

mvn -Pnexus package					打包

java -jar target\打包的包名				查看jar包里的文件

--logging.level.root=warn				取消日志

-Drun.arguments="--name=Daniel"		替换properties里name的属性

##### 修改端口号

在resources文件中的application.properties文件中添加:server.port=int;

int为自己输入的端口号

每次运行后要记得停止运行,不然会报端口号出现错误的信息

### Spring Boot 的核心功能

1. 独立运行的Spring 项目
   Spring Boot 可以以jar包的形式独立运行，运行一个Spring Boot 项目只需要通过 java -jar xx.jar 来运行。
2. 内嵌Servlet 容器
   Spring Boot 可以选择内嵌Tomcat、Jetty或Undertow，这样我们无须以war包形式部署项目。
3. 提供starter简化Maven 配置
   Spring 提供了一系列的starter pom 来简化Maven 的依赖加载。
4. 自动配置Spring
   Spring Boot 会根据在类路径中的jar包、类，为jar包里的类自动配置Bean，这样会极大地减少我们要使用的配置。Spring Boot只考虑了大多数的场景，并不是所有的场景。
5. 准生产的应用监控
   Spring Boot 提供基于http、ssh、telnet对运行时的项目进行监控。
6. 无代码生成和xml配置
   Spring Boot不是借助代码生成来实现的，而是通过条件注解来实现的，这是spring 4.x的新特性。Spring 4.x提倡使用Java配置和注解配置组合，而Spring Boot不需要任何xml配置即可实现Spring 的所有配置。

### 