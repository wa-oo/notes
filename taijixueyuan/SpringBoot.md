# SpringBoot

##### Springboot命令行

mvn -Pnexus spring-boot:run   		 运行springboot项目

mvn -Pnexus package				打包

java -jar target\打包的包名			查看jar包里的文件

##### 修改端口号

在resources文件中的application.properties文件中添加:server.port=int;

int为自己输入的端口号

每次运行后要记得停止运行,不然会报端口号出现错误的信息