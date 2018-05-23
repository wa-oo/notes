# 单元测试 @Test

JUnit是Java单元测试框架

Junit4通过注解的方式来识别测试方法

- @BeforeClass   全局只会执行一次,而且是第一个运行
- @Before   在测试方法运行之前运行
- @Test   测试方法
- @After   在测试方法运行之后允许
- @AfterClass   全局只会运行一次,而且是在最后一个运行
- @Ignore   忽略此方法

##### 导包

一般测试用到的三个包:

- hamcrest-core-1.3.jar 

- hamcrest-library-1.3.jar 

- junit-4.10.jar 

如果缺少会报如下错误

![1527083159780](C:\Users\WangTao\AppData\Local\Temp\1527083159780.png)

