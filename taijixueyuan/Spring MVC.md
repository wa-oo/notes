# Spring MVC

1. #### 接受参数

   ```java
   @Controller
   public class UserController {
   	
   	@RequestMapping(value="/save",method=RequestMethod.PUT)
   	public String save(User user) {
   		
   		System.out.println(user.toString());
   		return "success";
   	}
   }
   ```

   controller接受用户的请求,

   传统的接受参数

   

2. #### 传送参数

3. #### json

4. #### 文件上传

5. #### 后台校验