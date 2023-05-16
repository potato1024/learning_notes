## web注解

### @RestController

标在类前面，表明这是一个接收请求的类

@RestController=@Controller+@ResponseBody

### @ResponseBody

将controller的方法返回的对象通过适当的转换器转换为指定的格式之后，写入到response对象的body区，通常用来返回JSON数据或者是XML数据

### @RequestMapping("/hello")

标注在方法前面，处理请求地址映射

### public String simpleParam(@RequestParam(name = "name", required = false) String username, Integer age)

当请求参数名和controller方法中的形参名不相同，

在方法形参前面加上 @RequestParam 然后通过value属性执行请求参数名，从而完成映射。

默认required为true，必须接收参数，不传参会报错

```java
public Result page(@RequestParam(defaultValue = "1") Integer page,
                       @RequestParam(defaultValue = "10") Integer pageSize) 
```

defaultValue 属性用于设置默认接收参数

### public String listParam(@RequestParam List<String> hobby)

将多个请求参数的值封装到集合中（默认为数组）

### public String dateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime)

指定日期时间的传递格式

### public String jsonParam(@RequestBody User user)

用在实体对象之前，标识要封装的json对象

### @RequestMapping("/path/{id}/{name}")

### public String pathParam2(@PathVariable Integer id , @PathVariable String name)

路径参数

### @Component

Service层及Dao层的实现类，交给IOC容器管理

将当前类交给IOC容器来管理，成为IOC容器中的bean

**衍生注解：@Controller控制类、@Service业务类、@Repository数据访问类**

### @Autowired

为Controller及Service注入运行时依赖的对象

运行时，IOC容器会提供该类型的bean对象，并赋值给该变量

### @ComponentScan({"dao"},{"cpm.it"})

组件扫描注解，虽然没有显式配置，但是已经包含在启动类声明注解**@SpringBootApplication**中，默认扫描的范围是启动类所在包及其子包

### @Primary

当存在多个相同类型的Bean注入时，加上@Primary注解，来确定默认的实现

### @Qualifier("empServiceA")

使用@Qualifier注解：指定当前要注入的bean对象。 在@Qualifier的value属性中，指定注入的bean的名称。

@Qualifier注解不能单独使用，必须配合**@Autowired**使用

### @Resource(name = "empServiceB")

是按照bean的名称进行注入。通过name属性指定要注入的bean的名称。

### @GetMapping(value = "/depts")

指定请求方式为get，等效于

```java
@RequestMapping(value = "/depts", method = RequestMethod.GET)
```

###  @Value("${配置文件中的key}")

外部配置的属性注入，读取application.properties配置文件。

```java
    @Value("${aliyun.oss.endpoint}")
    private String endpoint;
```

### @ConfigurationProperties(prefix = "aliyun.oss")

将配置文件中配置项的值自动的注入到对象的属性中，通过perfect属性来指定配置参数项的前缀

### @Configuration

配置类

### RestControllerAdvice

定义全局异常处理器

@RestControllerAdvice = @ControllerAdvice + @ResponsBody

### @ExceptionHandler(Exception.class) 

通过@ExceptionHandler注解当中的value属性来指定我们要捕获的是哪一类型的异常

### @Transactional

Spring事务管理，可以书写在方法、类、接口上

rollbackFor = Exception.class（指定回滚的异常类型，默认为RunTimeException）

propagation = REQUIRED_NEW(挂起当前事务，建立新的事务；默认为REQUIRED，加入当前事务)

### @Aspect

标识当前类是一个AOP类

### @Around("execution(* com.itheima.service.\*.\*(..))")

标注在方法上，指定service下的所有类的所有方法

> - @Around：环绕通知，此注解标注的通知方法在目标方法前、后都被执行
> - @Before：前置通知，此注解标注的通知方法在目标方法前被执行
> - @After ：后置通知，此注解标注的通知方法在目标方法后被执行，无论是否有异常都会执行
> - @AfterReturning ： 返回后通知，此注解标注的通知方法在目标方法后被执行，有异常不会执行
> - @AfterThrowing ： 异常后通知，此注解标注的通知方法发生异常后执行

### @PointCut

```java
    //抽取
    @Pointcut("execution(* com.itheima.service.*.*(..))")
    private void pt(){
    }

    //使用公共切入点表达式
    @Before("pt()")
    public void before(JoinPoint joinPoint){
        log.info("before ...");
    }
```

### @Order(2)

切面类的执行顺序（前置通知：数字越小先执行; 后置通知：数字越小越后执行）

### @Target(ElementType.METHOD)

### @Retention(RetentionPolicy.RUNTIME)

自定义注解

###  @Before("@annotation(com.itheima.anno.MyLog)")

基于注解的方式来匹配切入点方法

### @Scope("prototype") 

bean作用域为非单例（默认singleton）

### @Lazy 

延迟加载

### @Bean

声明第三方Bean

    @Bean //将当前方法的返回值对象交给IOC容器管理, 成为IOC容器bean
    public SAXReader saxReader(){
        return new SAXReader();
    }

### @Import(TokenParser.class)

导入的类会被Spring加载到IOC容器中（普通类，配置类，ImportSelector接口实现类）

 ### @EnableXxxxx

- 第三方依赖中提供的注解

~~~java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Import(MyImportSelector.class)//指定要导入哪些bean对象或配置类
public @interface EnableHeaderConfig { 
}
~~~

- 在使用时只需在启动类上加上@EnableXxxxx注解即可

---

## mybatis注解

### @Mapper

表示是mybatis中的Mapper接口。程序运行时：框架会自动生成接口的实现类对象(代理对象)，并给交Spring的IOC容器管理

### @Select注解

select查询，用于书写select查询语句

### @Delete("delete from emp where id = #{id}")

使用#{key}方式获取方法中的参数值

---

## lombak注解

### @Getter/@Setter

为所有的属性提供get/set方法

### @ToString

会给类自动生成易阅读的  toString 方法

### @EqualsAndHashCode

根据类所拥有的非静态字段自动重写 equals 方法和  hashCode 方法

### @Data

提供了更综合的生成代码功能（@Getter  + @Setter + @ToString + @EqualsAndHashCode）

### @NoArgsConstructor

为实体类生成无参的构造器方法

### @AllArgsConstructor

为实体类生成除了static修饰的字段之外带有各参数的构造器方法。

### @Options(useGeneratedKeys = true,keyProperty = "id")

主键返回，封装到id属性中

### @Results注解

```java
@Results({@Result(column = "dept_id", property = "deptId"),
          @Result(column = "create_time", property = "createTime"),
          @Result(column = "update_time", property = "updateTime")})
```

数据封装，手动结果映射

### @Param("name") String name

在springBoot的1.x版本/单独使用mybatis（使用@Param注解来指定SQL语句中的参数名）

### @Slf4j

用于Logger对象的声明，替代以下语句

```java
    private static Logger log = LoggerFactory.getLogger(DeptController.class);
```

### @WebFilter(urlPatterns = "/*")

配置过滤器要拦截的请求路径（ /* 表示拦截浏览器的所有请求 ）

### @ServletComponentScan

标识在启动类上，开启SpringBoot项目对于Servlet组件的支持

