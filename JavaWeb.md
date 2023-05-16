## web模板

- 生成主体：==!==
- css外联：==link:css== 
- 空格：&nbsp

---

## JS

- 每行结尾的分号可有可无，建议书写

---

## Tips

0. 前端打包后的文件在vue-cli的dist文件夹下，将其部署在nginx下的html文件夹下

1. 声明bean的时候，可以通过value属性指定bean的名字，如果没有指定，默认为类名首字母小写

1. 如果mapper接口方法形参只有一个普通类型的参数，#{…} 里面的属性名可以随便写，如：#{id}、#{value}。但是建议保持名字一致。

1. #{...}会将#{…}替换为?，生成预编译SQL，会自动设置参数值

   - 使用时机：参数传递，都使用#{…}

1. ${...}拼接SQL。直接将参数拼接在SQL语句中，存在SQL注入问题

   - 使用时机：如果对表名、列表进行动态设置时使用

1. 使用Mybatis的注解，主要是来完成一些简单的增删改查功能。如果需要实现复杂的SQL功能，建议使用XML来配置映射语句。

1. XML配置文件规范：

   - XML映射文件的名称与Mapper接口名称一致，并且将XML映射文件和Mapper接口放置在相同包下（同包同名）
   - XML映射文件的namespace属性为Mapper接口全限定名一致
   - XML映射文件中sql语句的id与Mapper接口中的方法名一致，并保持返回类型一致。

1. 基于REST风格URL如下：通过URL定位要操作的资源，通过HTTP动词(请求方式)来描述具体的操作

   ```
   http://localhost:8080/users/1  GET：查询id为1的用户
   http://localhost:8080/users    POST：新增用户
   http://localhost:8080/users    PUT：修改用户
   http://localhost:8080/users/1  DELETE：删除id为1的用户
   ```

8. 开发流程：查看页面原型明确需求-阅读接口文档-思路分析-功能接口开发-功能接口测试-前后端联调测试

9. 一个完整的请求路径，应该是类上@RequestMapping的value属性 + 方法上的 @RequestMapping的value属性

8. 文件上传前端页面三要素：

- 表单必须有file域，用于选择要上传的文件

  > ~~~html
  > <input type="file" name="image"/>
  > ~~~

- 表单提交方式必须为POST

  > 通常上传的文件会比较大，所以需要使用 POST 提交方式

- 表单的编码类型enctype必须要设置为：multipart/form-data


> 普通默认的编码格式是不适合传输大型的二进制数据的，所以在文件上传时，表单的编码格式必须设置为multipart/form-data

11. 后端程序接收文件：

    Spring中提供了一个API：MultipartFile，使用这个API就可以来接收到上传的文件

    MultipartFile 常见方法： 

    - String  getOriginalFilename();  //获取原始文件名
    - void  transferTo(File dest);     //将接收的文件转存到磁盘文件中
    - long  getSize();     //获取文件的大小，单位：字节
    - byte[]  getBytes();    //获取文件内容的字节数组
    - InputStream  getInputStream();    //获取接收到的文件内容的输入流

12. 保证每次上传文件时文件名都唯一的（使用UUID获取随机文件名）

    ```java
            //获取原始文件名
            String originalFilename = image.getOriginalFilename();
    
            //构建新的文件名
            String extname = originalFilename.substring(originalFilename.lastIndexOf("."));//文件扩展名
            String newFileName = UUID.randomUUID().toString()+extname;//随机名+文件扩展名
    ```


13. 常见配置文件：

    xml：臃肿

    properties：层级结构不清晰

    yml/yaml：简洁，以数据为中心（推荐）

14. yml配置对象/Map集合：

    ```yml
    user:
      name: zhangsan
      age: 18
      password: 123456
    ```

    配置数组/List/Set集合

    ```yml
    hobby: 
      - java
      - game
      - sport
    ```

15. 简化配置类：

    - 需要创建一个实现类，且实体类中的属性名和配置文件当中key的名字必须要一致

    > 比如：配置文件当中叫endpoints，实体类当中的属性也得叫endpoints，另外实体类当中的属性还需要提供 getter / setter方法

    - 需要将实体类交给Spring的IOC容器管理，成为IOC容器当中的bean对象

    - 在实体类上添加`@ConfigurationProperties`注解，并通过perfect属性来指定配置参数项的前缀

16. 如果要注入的属性非常的多，并且还想做到复用，就可以定义这么一个bean对象。通过 configuration properties 批量的将外部的属性配置直接注入到 bean对象的属性当中

    如果注入的属性少，用value

17. 生成JWT代码实现：

    ~~~java
    @Test
    public void genJwt(){
        Map<String,Object> claims = new HashMap<>();
        claims.put("id",1);
        claims.put("username","Tom");
        
        String jwt = Jwts.builder()
            .setClaims(claims) //自定义内容(载荷)          
            .signWith(SignatureAlgorithm.HS256, "itheima") //签名算法        
            .setExpiration(new Date(System.currentTimeMillis() + 24*3600*1000)) //有效期   
            .compact();
        
        System.out.println(jwt);
    }
    ~~~

    解码：

    

    ~~~java
    @Test
    public void parseJwt(){
        Claims claims = Jwts.parser()
            .setSigningKey("itheima")//指定签名密钥（必须保证和生成令牌时使用相同的签名密钥）  
    	    .parseClaimsJws("eyJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjcyNzI5NzMwfQ.fHi0Ub8npbyt71UqLXDdLyipptLgxBUg_mSuGJtXtBk")
            .getBody();
    
        System.out.println(claims);
    }
    ~~~


18. Filter（javax.servlet）

    init和destroy有默认实现

    放行

    ```java
        //放行请求
        filterChain.doFilter(servletRequest,servletResponse);
    ```

19. 以注解方式配置的Filter过滤器，它的执行优先级是按时过滤器类名的自动排序确定的，类名排名越靠前，优先级越高

20. 定义拦截器LoginCheckInterceptor，实现HandlerInterceptor，重写三个方法，标注@Component，交给IOC管理

    配置拦截器WebConfig，实现WebMvcConfigure，加上注解@Configuration，重写方法addInterceptors注册拦截器，调用registry的，addInterceptor方法添加拦截器，再调addPathPatterns指定要拦截的资源，调用excludePathPatterns指定不需要拦截哪些资源

21. 拦截所有资源，filter用/*，interceptor用/**（/\*拦截一级路径）

22. 全局异常处理器：优雅

23. Spring事务管理@Transactional：在当前这个方法执行开始之前来开启事务，方法执行完毕之后提交事务。如果在这个方法执行的过程当中出现了异常，就会进行事务的回滚操作。

    @Transactional注解：我们一般会在业务层当中来控制事务，因为在业务层当中，一个业务功能可能会包含多个数据访问的操作。在业务层来控制事务，我们就可以将多个数据访问操作控制在一个事务范围内。

    书写位置：

    - 方法
      - 当前方法交给spring进行事务管理
    - 类
      - 当前类中所有的方法都交由spring进行事务管理
    - 接口
      - 接口下所有的实现类当中所有的方法都交给spring 进行事务管理

    （一般加在业务层的增删改方法上）

24. 连接点JoinPoint，可以被AOP控制的方法（暗含方法执行时的相关信息）

    通知：Advice，指哪些重复的逻辑，也就是共性功能（最终体现为一个方法）

    切入点：PointCut，匹配**连接点**的条件，通知仅会在切入点方法执行时被应用

    切面：Aspect，描述通知与切入点的对应关系（通知+切入点）

    标对象：Target，通知所应用的对象

25. 在使用通知时的注意事项：

    - @Around环绕通知需要自己调用 ProceedingJoinPoint.proceed() 来让原始方法执行，其他通知不需要考虑目标方法执行
    - @Around环绕通知方法的返回值，必须指定为Object，来接收原始方法的返回值，否则原始方法执行完毕，是获取不到返回值的。

26. 切入点表达式：

    ```
    execution(访问修饰符?  返回值  包名.类名.?方法名(方法参数) throws 异常?)
    ```

    - `*` ：单个独立的任意符号，可以通配任意返回值、包名、类名、方法名、任意类型的一个参数，也可以通配包、类、方法名的一部分
    - `..` ：多个连续的任意符号，可以通配任意层级的包，或任意类型、任意个数的参数
    - 根据业务需要，可以使用 且（&&）、或（||）、非（!） 来组合比较复杂的切入点表达式。

27. 切入点表达式的书写建议：

    - 所有业务方法名在命名时尽量规范，方便切入点表达式快速匹配。如：查询类方法都是 find 开头，更新类方法都是update开头

    - 描述切入点方法通常基于接口描述，而不是直接描述实现类，增强拓展性
    - 在满足业务需要的前提下，尽量缩小切入点的匹配范围。如：包名匹配尽量不使用 ..，使用 * 匹配单个包

28. 配置优先级：命令行参数>java系统属性>properties>yml>yaml

29. scope标签的取值范围：

    | **scope**值     | **主程序** | **测试程序** | **打包（运行）** | **范例**    |
    | --------------- | ---------- | ------------ | ---------------- | ----------- |
    | compile（默认） | Y          | Y            | Y                | log4j       |
    | test            | -          | Y            | -                | junit       |
    | provided        | Y          | Y            | -                | servlet-api |
    | runtime         | -          | Y            | Y                | jdbc驱动    |

---

## 概念

element

yapi

ajax

axios

vue-cli

OSS

---

## 配置

### 日志输入

mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl

### 驼峰映射

mybatis.configuration.map-underscore-to-camel-case=true

### 上传大文件

#配置单个文件最大上传大小
spring.servlet.multipart.max-file-size=10MB

#配置单个请求最大上传大小(一次请求可以上传多个文件)
spring.servlet.multipart.max-request-size=100MB

### 事务控制日志

```yml
logging:
  level:
    org.springframework.jdbc.support.JdbcTransactionManager: debug
```



---

## Web课程第137集前端部署问题汇总（4月26日）

**问题：后端代码开发好查询功能之后，使用postman测试正常，前后端联调时，前端代码加载异步请求时出错，不能获取后端数据库的内容展示在前端页面。**

使用的前端工程为开发好的，直接放在本地nginx下的html文件夹下。

弹幕反馈是使用自己的nginx配置不行，必需用资料中提供的nginx文件夹启动nginx.exe（但是mac不能直接使用）

本人测试了提供的前端vue-project和提供的nignx文件夹中的前端工程，都不能成功。

随后本人使用vscode启动了提供的前端vue-project，又遇到了**第二个问题：node环境，报错信息中反馈了...not supported**，问题在于node18中加强了安全技术，原工程在node16中开发。

经过一番折腾，下载了nvm管理node的版本，node use 16可以切换到16版本，但是vscode终端的版本难以控制（一直是18），最终使用命令行进入工程目录，npm run dev运行到浏览器，又遇到了**第三个问题：...not permitted**，这是由于工程文件未被允许修改导致的，进入文件后修改全部权限为读与写。

再次npm run dev，发现加载数据成功，即前端工程没问题，可以实现联调。

所以原因在于nginx的配置上，在于没有复制资料中提供的nginx.conf，有些配置和默认的不太一样（应该是反向代理），复制替换之后成功

之间还遇到了第四个问题：nginx环境报错，stop和reload命令都不能正常进行，导致不管怎么配置html文件夹，页面始终不变，后通过重新编译运行解决。

[不使用brew配置](https://blog.csdn.net/qq_37958208/article/details/116467213)
