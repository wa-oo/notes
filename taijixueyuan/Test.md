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

![image](https://github.com/wangtao-Allen/notes/blob/master/photo/test-error.png)

原因：
1.有返回值的方法不能直接测试

2.带参数的方法不能直接测试

3.访问权限在public一下的方法不能直接测试

4.static静态方法不能直接测试

5.不能给出现前四个条件中任意一个的方法添加@Test注解，否则执行满足@Test条件的方法也会出现initializationerror初始化异常
