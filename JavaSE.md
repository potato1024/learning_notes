## IDEA mac 快捷键

- 格式化代码：==cmd+opt+L==
- 多行注释：==cmd+opt+/==或者==cmd+shift+/==
- 查看参数调用情况：==cmd+p==
- 抽取代码为方法：==cmd+opt+m==
- 批量修改变量名：==shift+f6==
- 对象接收：==cmd+opt+v==或者==.var==
- 包裹代码块：==cmd+opt+t==
- 全局查找（nevigate）：==shift+shift==
- 自动生成getset方法：==cmd+n==或者==ctrl+return==
- 向下复制一行：==cmd+d==
- 竖排选中：==opt不松==
- 跟进：==cmd+b==
- 接口的实现类：==cmd+opt+b==
- 返回：==cmd+opt+左==或者==cmd+[==
- 变量切割：==opt+return==
- 整行移动：==shift+opt+上下==
- 撤销：==cmd+shift+z==
- run：==ctrl+shift+r==
- debug：==ctrl+shift+d==
- 重写方法：==ctrl+o==
- 显示当前类的所有方法：==cmd+f12==或者==cmd+7==
- 查看变量的值（调试中）：==cmd+f8==
- xml标签自闭合：==opt+shift+return==
- xml标签展开：==opt+return==
- 排除maven依赖：==shift+fn+delete==
- 查看类的实现：==ctrl+H==
- 查看方法调用者：==ctrl+opt+H==
- 大小写转换：==cmd+shift+u==

---

## IDEA 代码模板

- 主函数：==psvm、main==
- 输出语句：==sout==或者==.sout==
- 输出占位语句：==souf（使用%s占位）==
- 循环：==.fori==
- 倒序遍历：==.forr==
- 对象接收：==.var==
- 增强for：==iter==或者==.for==
- 迭代器：==itit==

---

## 常见API

### String

- 提取字符：==chatAt==
- 分割字符：==substring==
- 替换：==replace==
- 生成字符数组：==tochararray==
- 忽略大小写的比较：==equalsIgnoreCase==
- 正则比较：==matches==

### StringBuilder

- 添加：==append==
- 反转：==reverse==

### Stringjoiner

- 构造：==new Stringjoiner("---")==或者==new Stringjoiner(", ", "[","]" )==
- 添加：==add==

### Math

```java
public static int abs(int a)					// 返回参数的绝对值
public static double ceil(double a)				// 返回大于或等于参数的最小整数
public static double floor(double a)			// 返回小于或等于参数的最大整数
public static int round(float a)				// 按照四舍五入返回最接近参数的int类型的值
public static int max(int a,int b)				// 获取两个int值中的较大值
public static int min(int a,int b)				// 获取两个int值中的较小值
public static double pow (double a,double b)	// 计算a的b次幂的值
public static double random()					// 返回一个[0.0,1.0)的随机值
```

### System

```java
public static long currentTimeMillis()			// 获取当前时间所对应的毫秒值（当前时间为0时区所对应的时间即就是英国格林尼治天文台旧址所在位置）
public static void exit(int status)				// 终止当前正在运行的Java虚拟机，0表示正常退出，非零表示异常退出
public static native void arraycopy(Object src,  int  srcPos, Object dest, int destPos, int length); // 进行数值元素copy
```

### Runtime

```java
public static Runtime getRuntime()		//当前系统的运行环境对象
public void exit(int status)			//停止虚拟机
public int availableProcessors()		//获得CPU的线程数
public long maxMemory()				    //JVM能从系统中获取总内存大小（单位byte）
public long totalMemory()				//JVM已经从系统中获取总内存大小（单位byte）
public long freeMemory()				//JVM剩余内存大小（单位byte）
public Process exec(String command) 	//运行cmd命令
```

### Object

```java
public String toString()				//返回该对象的字符串表示形式(可以看做是对象的内存地址值)
public boolean equals(Object obj)		//比较两个对象地址值是否相等；true表示相同，false表示不相同
protected Object clone()    			//对象克隆
```

### Objects

```java
public static String toString(Object o) 					// 获取对象的字符串表现形式
public static boolean equals(Object a, Object b)			// 比较两个对象是否相等
public static boolean isNull(Object obj)					// 判断对象是否为null
public static boolean nonNull(Object obj)					// 判断对象是否不为null
```

### BigInteger

构造方法

```java
public BigInteger(int num, Random rnd) 		//获取随机大整数，范围：[0 ~ 2的num次方-1]
public BigInteger(String val) 				//获取指定的大整数
public BigInteger(String val, int radix) 	//获取指定进制的大整数
    
下面这个不是构造，而是一个静态方法获取BigInteger对象
public static BigInteger valueOf(long val) 	//静态方法获取BigInteger的对象，内部有优化
```

成员方法

```java
public BigInteger add(BigInteger val)					//加法
public BigInteger subtract(BigInteger val)				//减法
public BigInteger multiply(BigInteger val)				//乘法
public BigInteger divide(BigInteger val)				//除法
public BigInteger[] divideAndRemainder(BigInteger val)	 //除法，获取商和余数
public  boolean equals(Object x) 					    //比较是否相同
public  BigInteger pow(int exponent) 					//次幂、次方
public  BigInteger max/min(BigInteger val) 				//返回较大值/较小值
public  int intValue(BigInteger val) 					//转为int类型整数，超出范围数据有误
```

###	BigDecimal

```java
public BigDecimal add(BigDecimal value)				// 加法运算
public BigDecimal subtract(BigDecimal value)		// 减法运算
public BigDecimal multiply(BigDecimal value)		// 乘法运算
public BigDecimal divide(BigDecimal value)			// 除法运算
public double doubleValue()											//转为double类型
public BigDecimal setScale(int newScale, RoundingMode roundingMode) //保留小数
```

### Pattern、Matcher

```java
//获取正则表达式的对象
Pattern p = Pattern.compile("Java\\d{0,2}");
//获取文本匹配器的对象
Matcher m = p.matcher(str);
//拿着文本匹配器从头开始读取，寻找是否有满足规则的子串
boolean b = m.find();
//方法底层会根据find方法记录的索引进行字符串的截取
String s1 = m.group();

//方法底层会根据find方法记录的索引进行字符串的截取，获取第index组
String s1 = m.group(int index);
```

### Collection

| 方法名                     | 说明                               |
| :------------------------- | :--------------------------------- |
| boolean add(E e)           | 添加元素                           |
| boolean remove(Object o)   | 从集合中移除指定的元素             |
| boolean removeIf(Object o) | 根据条件进行移除                   |
| void   clear()             | 清空集合中的元素                   |
| boolean contains(Object o) | 判断集合中是否存在指定的元素       |
| boolean isEmpty()          | 判断集合是否为空                   |
| int   size()               | 集合的长度，也就是集合中元素的个数 |

### List

| 方法名                          | 描述                                   |
| ------------------------------- | -------------------------------------- |
| void add(int index,E   element) | 在此集合中的指定位置插入指定的元素     |
| E remove(int   index)           | 删除指定索引处的元素，返回被删除的元素 |
| E set(int index,E   element)    | 修改指定索引处的元素，返回被修改的元素 |
| E get(int   index)              | 返回指定索引处的元素                   |

### LinkedList

| 方法名                    | 说明                             |
| ------------------------- | -------------------------------- |
| public void addFirst(E e) | 在该列表开头插入指定的元素       |
| public void addLast(E e)  | 将指定的元素追加到此列表的末尾   |
| public E getFirst()       | 返回此列表中的第一个元素         |
| public   E getLast()      | 返回此列表中的最后一个元素       |
| public E removeFirst()    | 从此列表中删除并返回第一个元素   |
| public   E removeLast()   | 从此列表中删除并返回最后一个元素 |

### Arrays

```java
public static String tostring（数组）		//把数组拼接成一个字符串
public static int binarySearch(数组，查找的元素）		//二分查找法查找元素
public static int[] copyof(原数组，新数组长度）		//拷贝数组
public static int[] copyOfRange(原数组，起始索引，结束索引）		//拷贝数组（指定范围）
public static void fill(数组，元素）		//填充数组
public static void sort(数组）		//按照默认方式进行数组排序
public static void sort(数组，排序规则）		//按照指定的规则排序
```

### Map

| 方法名                              | 说明                                 |
| ----------------------------------- | ------------------------------------ |
| V   put(K key,V   value)            | 添加元素                             |
| V   remove(Object key)              | 根据键删除键值对元素                 |
| void   clear()                      | 移除所有的键值对元素                 |
| boolean containsKey(Object key)     | 判断集合是否包含指定的键             |
| boolean containsValue(Object value) | 判断集合是否包含指定的值             |
| boolean isEmpty()                   | 判断集合是否为空                     |
| int size()                          | 集合的长度，也就是集合中键值对的个数 |

### Collections

```java
public static <T> boolean addA11(Collection<T> c， T...elements） 	//批量添加元素
public static void shuffle(List‹?> list)		//打乱List集合元素的顺序
public static <T> void sort(List‹T> list)		//排序
public static <T> void sort(List<T> list, Comparator<T> c)		//根据指定的规则进行排序
public static <T> int binarysearch (List<T> list, T key)		//以二分查找法查找元素
public static <T> void copy (List<T> dest, List<T> src)		//拷贝集合中的元素
public static <T> int fill (List<T> list, T obj)		//使用指定的元素填充集合
public static <T> void max/min(Collection‹T> coll)		//根据默认的自然排序获取最大/小值
public static <T> void swap(List‹?> list, int i, int j)		//交换集合中指定位置的元素
```

### Stream

中间方法

```java
Stream<T> filter(Predicate<? super T> predicate)		//过滤
Stream<T> limit(long maxSize)		//获取前几个元素
Stream<T> skip(long n)		//跳过前几个元素
Stream<T> distinct		//元素去重，依赖(hashcode和equals方法）
static <T> Stream<T> concat(Stream a, Stream b)		//合并a和b两个流为一个流
Stream<R> map(Function<T, R> mapper)		//转换流中的数据类型
```

终结方法

```java
void forEach(Consumer action)		//遍历
long count()		//统计
toArray()		//收集流中的数据，放到数组中
collect(Collector collector)		//收集流中的数据，放到集合中
```

### Exception

```java
public String getMessage ()		//返回此 throwable 的详细消息字符串
public String toString()		//返回此可抛出的简短描述
public void printStackTrace()		//把异常的错误信息输出在控制台
```

### File

```java
public File(String pathname)                //根据文件路径创建文件对象
public File(String parent, String child)    //根据父路径名字符串和子路径名字符串创建文件对象
public File(File  parent, String child)     //根据父路径对应文件对象和子路径名字符串创建文件对象
```

```java
public boolean isDirectory()        //判断此路径名表示的File是否为文件夹
public boolean isFile()             //判断此路径名表示的File是否为文件
public boolean exists()             //判断此路径名表示的File是否存在
public long length()                //返回文件的大小（字节数量）
public String getAbsolutePath()     //返回文件的绝对路径
public String getPath()             //返回定义文件时使用的路径
public String getName()             //返回文件的名称，带后缀
public long lastModified()          //返回文件的最后修改时间（时间毫秒值）
```

```java
public boolean createNewFile()      //创建一个新的空的文件
public boolean mkdir()              //创建单级文件夹
public boolean mkdirs()             //创建多级文件夹
public boolean delete()             //删除文件、空文件夹
```

```java
public File[] listFiles()       //获取当前该路径下所有内容
public static File[] listRoots()               //列出可用的文件系统根
public String[] list()                         //获取当前该路径下所有内容
public String[] list(FilenameFilter filter)    //利用文件名过滤器获取当前该路径下所有内容
public File[] listFiles(FileFilter filter)     //利用文件名过滤器获取当前该路径下所有内容
public File[] listFiles(FilenameFilter filter) //利用文件名过滤器获取当前该路径下所有内容 
```

### FileOutputStream

```java
void write(int b)                       //一次写一个字节数据
void write(byte[] b)                    //一次写一个字节数组数据
void write(byte[] b, int off, int len)  //一次写一个字节数组的部分数据
```

### FileInputStream

```java
public int read()												//一次读一个字节数据
public int read(byte[] buffer)					//一次读一个字节数组数据
```

### FileReader

```java
public int read()                   //读取数据，读到末尾返回-1
public int read(char[] buffer)      //读取多个数据，读到末尾返回-1
```

### FileWriter

```java
void write(int c)                           //写出一个字符
void write(String str)                      //写出一个字符串
void write(String str, int off, int len)    //写出一个字符串的一部分
void write(char[] cbuf)                     //写出一个字符数组
void write(char[] cbuf, int off, int len)   //写出字符数组的一部分
```

### BufferedReader

```java
public String readLine()			//读取一行数据，如果没有数据可读了，会返回null 
```

### BufferedWriter

```java
public void newLine()					//跨平台的换行
```

### ObjectOutputStream

```java
public final void writeObject(Object obj)           //把对象序列化（写出）到文件中去
```

### ObjectInputStream

```java
public Object readObject()     							//把序列化到本地文件中的对象，读取到程序中来
```

### PrintStream

构造方法

```java
 public PrintStream(OutputStream/File/String)            //关联字节输出流/文件/文件路径
 public PrintStream(String fileName, Charset charset)    //指定字符编码
 public PrintStream(OutputStreamout, boolean autoFlush)  //自动刷新
 public PrintStream(OutputStream out, boolean autoFlush, String encoding)    //指定字符编码且自动刷新
```

成员方法

```java
 public void write(int b)            //常规方法：规则跟之前一样，将指定的字节写出
 public void println(Xxx xx)         //特有方法：打印任意数据，自动刷新，自动换行
 public void print(Xxx xx)           //特有方法：打印任意数据，不换行
 public void printf(String format, Object... args)   //特有方法：带有占位符的打印语句，不换行
```

### ZipInputStream

```java
public ZipEntry getNextEntry() 				//返回一个ZipEntry对象，没有返回null
public void closeEntry()							//关闭当前ZipEntry对象，表示在压缩包中的一个文件处理完毕了
```

### ZipOutputStream

```java
public void putNextEntry(ZipEntry e)			//将一个ZipEntry对象放到压缩包中
```

### commons.io.FileUtils

```java
static void copyFile(File srcFile, File destFile)                   //复制文件
static void copyDirectory(File srcDir, File destDir)                //复制文件夹
static void copyDirectoryToDirectory(File srcDir, File destDir)     //复制文件夹
static void deleteDirectory(File directory)                         //删除文件夹
static void cleanDirectory(File directory)                          //清空文件夹
static String readFileToString(File file, Charset encoding)         //读取文件中的数据变成成字符串
static void write(File file, CharSequence data, String encoding)    //写出数据
```

### commons.io.IOUtils

```java
public static int copy(InputStream input, OutputStream output)      //复制文件
public static int copyLarge(Reader input, Writer output)            //复制大文件
public static String readLines(Reader input)                        //读取数据
public static void write(String data, OutputStream output)          //写出数据
```

### hutool.core.io.FileUtil

```java
file：根据参数创建一个file对象
touch：根据参数创建文件
  
writeLines：把集合中的数据写出到文件中，覆盖模式。
appendLines：把集合中的数据写出到文件中，续写模式。
readLines：指定字符编码，把文件中的数据，读到集合中。
readUtf8Lines：按照UTF-8的形式，把文件中的数据，读到集合中
  
copy：拷贝文件或者文件夹
```

### Thread

```java
String getName()                    //返回此线程的名称
void setName(String name)           //设置线程的名字（构造方法也可以设置名字）
static Thread currentThread()       //获取当前线程的对象
static void sleep(long time)        //让线程休眠指定的时间，单位为毫秒
setPriority(int newPriority)        //设置线程的优先级(默认为5，最低为1，最高为10)
final int getPriority()             //获取线程的优先级
final void setDaemon(boolean on)    //设置为守护线程(当其他的非守护线程执行完毕之后，守护线程会陆续结束)
public static void yield()      		//出让线程/礼让线程(表示出让当前CPU的执行权)
public final void join()  					//插入线程/插队线程(表示把调用者线程，插入到当前线程之前)
```

### Lock

```java
void lock()：获得锁
void unlock()： 释放锁
```

### 锁对象Object(让当前线程跟锁进行绑定)

```java
void wait():当前线程等待，直到被其他线程唤醒
void notify():随机唤醒单个线程
void notifyAll():唤醒所有线程
```

### BlockingQueue<E>

```java
void put(E e):放入队列，底层有一个Lock锁
E take():从队列中取出，底层有一个Lock锁
```

### Executors

```java
public static ExecutorService newCachedThreadPool ()	//创建一个没有上限的线程池
public static ExecutorService newFixedThreadPool(int Threads)		//创建有上限的线程池
```

### ExecutorService

```java
Future<?> submit(Runnable task)					//提交任务
void shutdown();												//销毁线程池
```









---

## 概念

- 字面量
- JavaBean（插件：PTG）
- OGNL对象导航图
- 全类名、全限定名
- entry对象
- UTF：Unicode Transfer Format
- BOM头
- 超线程技术

---

## Tips

1. 在一条语句中，可以定义多个变量，影响阅读，不推荐

==int a = 10, b = 20, c = 20,d = 20;==

2. float -> F

   long -> L

3. project - module - package - class

   JDK - JRE - JVM

4. 隐式转换：byte - short - int - long - float - double

   byte、short、char三种类型的数据在运算的时候，都会直接先提升为int，然后再进行运算。

5. ++a：先自增，再参与计算

   a++：先参与计算，再自增

6. &&、||：短路运算符：前面满足条件，不计算后面，提高效率。所以一般不用&、|

7. if后的语句如果只有一条，可以不写大括号，但是一般不要省略。

8. 布尔类型判断不要写==if(flag == true)==，直接判断==if(flag)==

9. switch语句不写break会发生case穿透，有时可以对其进行利用。

   在JDK12的新特性：

   > switch (week) {
   >  case 1, 2, 3, 4, 5 -> System.out.println("工作日");
   >  case 6, 7 -> System.out.println("休息日");
   >  default -> System.out.println("没有这个星期");
   > }

​		JDK14: 对switch的结果整体赋值：

> String text = switch(day){
>
> case MON, TUE, WEN -> "上半周";
>
> case THU, FRI -> "下半周";
>
> case SAT, SUN -> "周末";
>
> }; 

10. 知道循环次数或者循环范围，用for。

    不知道循环次数和循环范围，但知道循环的结束条件，用while。

    一般不用do...while

11. 数组的定义：

    ==int [] array==或者==int array []==，一般用第一种

    静态初始化：==int[] arr = new int[]{11,22,33};==，一般省略为==int[] arr ={11,22,33};==

    动态初始化：==int[] arr = new int[3]==

12. 方法：

```java
public static void method (    ) {
  	// 方法体;
  }
```

​		方法重载只看传入参数的位置和类型，和方法的返回无关

13. 类：

    ```java
    public class Phone {
        //成员变量
        private String brand;
    
        //成员方法
        public void call() {   
           System.out.println("打电话");
        }
    }
    ```

    如果定义了构造方法，系统将不再提供默认的构造方法

    无论是否使用，都手工书写无参数构造方法

14. 创建字符串的方式：

    ```String s = “abc”；直接赋值```

    检查字符串常量池中有没有字符串abc，如果有，不会创建新的，而是直接复用。如果没有abc，才会创建一个新的

    ```String s1 = new String（“abc”）；```

    通过 new 创建的字符串对象，每一次 new 都会申请一个内存空间，虽然内容相同，但是地址值不同

15. 对于基本数据类型：==比的是具体的数值是否相等。

    对于引用数据类型：==比的是地址值是否相等。

16. 集合：长度可以变化，只能存储引用数据类型。

    添加基本数据类型时，需要使用其对应的包装类型（jdk5后自动装箱）

17. Scanner:

    第一个细节

    > next(), nextLine()接收任意数据，但是都返回字符串
    >
    > nextInt()接收整数，录入小数或其他字母会报错
    >
    > nextDouble()接收整数和小数，但是都返回小数，录入字母会报错

    第二个细节

    > next（），nextInt（），nextDouble（）在接收数据的时候，会遇到空格，回车，制表符其中一个就会停止接收数据，但是剩余的数据还在内存中，会在下次被接收
    >
    > nextLine（）方法是把一整行全部接收完毕

​		第三个细节

> 上述两套方案不能混用，否则会导致nextLine接收不到数据，如果想要整数，可以先接收，再使用Integer.parseInt进行类型转换

18. 退出程序：

    System.exit(0) 停止虚拟机运行

    break loop 退出循环（给循环命名为loop，仅使用break则跳出单层switch）

19. ```
    //开发细节：先验证格式是否正确，再验证是否唯一
    //         因为在以后所有的数据，都是存在数据库中，如果我们要校验，需要使用到网络资源。
    ```

20. ```
    //封装思想的应用：
    //我们可以把一些零散的数据，封装成一个对象
    //以后传递参数的时候，只要传递一个整体就可以了，不需要管这些零散的数据。
    ```

21. 静态变量是随着类的加载而加载的，优先于对象出现

    所有对象==共享==

    可以用类名调用，也可以用对象名调用，推荐使用类名调用

22. 静态方法多用于测试类或工具类中，javabean中很少使用

    javabean类：用来描述一类事物的类

    测试类：用来检查其他类是否书写正确，一般带有main方法，是程序的主入口

    工具类：不是用来描述一类事物，而是帮我们完成一些事情的类

23. 工具类：

    类名见名知意，私有化构造方法，方法全部定义为静态

24. 静态方法中没有this关键字（非静态的方法中隐藏了一个当前类的this参数，由虚拟机赋值）静态方法中，只能访问静态

    非静态方法可以访问所有

25. 当类与类之间，存在相同（共性）的内容，并满足子类是父类的一种，就可以考虑使用继承，来优化代码。

26. java中只支持单继承，不支持多继承，但是支持多层继承

27. 一个java文件中只写一个类

28. public修饰的类的类名与文件名一致

29. 栈与方法有关，堆与new有关，方法区与字节码文件有关

30. 虚方法表：非private，非static，非final

    只有父类中的虚方法才能被子类继承

31. 子类不能继承父类的构造方法。

    值得注意的是子类可以继承父类的私有成员（成员变量，方法），只是子类无法直接访问而已，可以通过getter/setter方法访问父类的private成员变量。

32. 成员变量的访问特点：就近原则（先在局部位置找，本类成员位置找，父类成员位置找，逐级往上）

33. 在子类中，最多只能调用一个super，super.super会报错

34. 成员方法的访问特点：直接调用满足就近原则，super调用直接访问父类

35. @Override是放在重写后的方法上，校验子类重写时语法是否正确

36. 方法重写的本质：覆盖虚方法表中的方法

37. 方法重写的注意事项和要求：

    > 1 重写方法的名称、形参列表必须与父类中的一致
    >
    > 2 子类重写父类方法时，访问权限子类必须大于等于父类（暂时了解：空着不写 < protected < public）
    >
    > 3 子类重写父类方法时，返回值类型子类必须小于等于父类
    >
    > 4 **建议：重写的方法尽量和父类保持一致**
    >
    > 5 只有被添加到虚方法表中的方法才能被重写

38. 构造方法的访问特点：

    > 子类不能继承父类的构造方法，但是可以通过super调用
    >
    > 子类构造方法的第一行，有一个默认的super()
    >
    > 默认先访问父类中无参的构造方法，再执行自己。
    >
    > 如果想要访问父类有参构造，必须手动书写。

39. this：理解为一个变量，表示当前方法调用者的地址值

super：代表父类存储空间

40. 使用this()调用本类的构造方法时，虚拟机不会再添加super()

41. 多态的前提：有继承/实现关系

    有父类引用指向子类对象

    有方法重写

42. 多态调用成员变量：编译看左边，运行也看左边

    多态调用成员方法：编译看左边，运行看右边

43. 多态的优势：方法中，使用父类型作为参数，可以接收所有子类对象

    多态的弊端：不能使用子类的特有功能

    强制类型转换：可以转换成真正的子类类型，从而调用子类独有功能

    转换类型与真实对象类型不一致会报错

44. 转换的时候用instanceof关键字判断：

    ```java
            if(a instanceof Dog){
                Dog d = (Dog) a;
                d.lookHome();
            }else if(a instanceof Cat){
                Cat c = (Cat) a;
                c.catchMouse();
            }else{
                System.out.println("没有这个类型，无法转换");
            }
    ```

    jdk14新特性：

    ```java
            if(a instanceof Dog d){
                d.lookHome();
            }else if(a instanceof Cat c){
                c.catchMouse();
            }else{
                System.out.println("没有这个类型，无法转换");
            }
    ```

45. final修饰方法：表明该方法是最终方法，不能被重写

    修饰类：表明该类是最终类，不能被继承

    修饰变量：叫做常量，只能被赋值一次

46. 常量命名规则：单个单词全用大写，多个单词用下划线隔开

47. 权限修饰符：实际开发中，一般只用private和public

    成员变量私有，方法公开

    特例：如果方法中的代码是抽取其他方法中共性代码，这个方法一般也私有

48. 局部代码块：提前结束变量的生命周期

    构造代码块：抽取构造方法中的重复代码（先执行构造方法块再执行构造方法）

    静态代码块：数据的初始化（随着类的加载而加载，并且只执行一次）

49. 构造代码块不够灵活，如果只有部分构造方法有重复代码，用构造代码块也会全部执行。

    可以将重复部分写在一个构造方法中用this(调用)，或者将重复代码抽取成为公共方法

50. 抽象类：

    抽取共性时，无法确定方法体，就把方法定义为抽象的

    强制让子类按照某种格式重写

    抽象方法所在的类，必须是抽象类

    抽象类不能实例化，可以有构造方法（给子类对象赋值用的）

    抽象类的子类要么重写所有抽象方法，要么是抽象类

51. 接口就是一种规则，是对行为的抽象

    接口的实现类要么重写所有抽象方法，要么是抽象类

    可以单实现，也可以多实现，还可以在继承一个类的同时实现多个接口

52. 接口中成员的特点：

    成员变量：只能是常量，默认修饰符 public static final

    构造方法：没有

    成员方法：只能是抽象方法，默认修饰符public abstract

    （jdk8新特性：接口中可以定义有方法体的方法）

    （jdk9新特性：接口中可以定义私有方法）

53. 实现多个接口时，如果有重名方法，只需要重写一次即可

54. 接口和接口之间可以单继承，也可以多继承，如果实现类实现了最下面的子接口，那么就需要重写体系中所有的抽象方法

55. 细节：如果不想让外界去直接创建对象，或者创建这个类的对象是没有意义的，可以把一个类定义为抽象类

56. 接口的默认方法（jdk8）：解决接口升级问题

    默认方法不是抽象方法，不强制重写，如果重写则去掉default关键字

    public可以省略，default不能省略

    如果实现了多个接口，多个接口中存在同名的默认方法，子类就必须对该方法进行重写

57. 接口的静态方法（jdk8）

    public可以省略，static不能省略

    静态方法只能通过接口名调用，不能通过实现类或对象名调用

58. 接口的私有方法（jdk9）：重复代码只为当前接口提供服务，不需要外类访问

    普通的私有方法，给默认方法服务

    静态的私有方法，给静态方法服务

59. 接口多态：当一个方法的参数是接口时，可以传递接口所有实现类的对象

60. 适配器设计模式：

    编写中间类XXXAdapter（用abstract修饰），实现对应的接口，对接口中的抽象方法进行空实现

    让真正的实现类继承中间类，并重写需要使用的方法

61. 内部类表示的事物是外部类的一部分，内部类单独出现没有任何意义

    内部内可以直接访问外部类的成员，包括私有

    外部类要访问内部类的成员，必须创建对象

62. jdk16新特性：在成员内部类的里面，可以定义静态变量

63. ```java
    Outer.Inner oi = new Outer().new Inner();
               System.out.println(Outer.this.a);
    ```

64. 静态内部类只能访问外部类中的静态变量和静态方法，如果想要访问非静态的需要创建对象

65. ```java
    Outer.Inner oi = new Outer.Inner();//创建静态内部类的对象
    oi.show1();//非静态方法
    Outer.Inner.show2();//静态方法
    ```

66. 局部内部类：将内部类定义在方法里面，类似于方法里面的局部变量

67. 匿名内部类的本质：隐藏了名字的内部类，可以写在成员位置，也可以写在局部位置

    包含了继承或实现、方法重写、创建对象

    如果子类或实现类只用一次，可以用匿名内部类简化代码

68. ```java
            new Swim() {
                @Override
                public void swim() {
                    System.out.println("swim");
                }
            };
    ```

69. 长度固定用数组，长度不固定用集合

70. 相对路径是相对项目而言的，从模块名开始书写

71. 如果一个接口里面没有抽象方法，表示当前接口是一个标记性接口

    Cloneable表示一旦实现，当前类的对象可被克隆，如果没有实现，刚不可被克隆

72. 浅克隆：不管对象内部的属性是基本数据类型还是引用数据类型，都完全拷贝过来

    深克隆：基本数据类型拷贝过来，字符串复用，引用数据类型会重新创建新的

73. BigInteger使用valueof时底层对-16～16做了优化，节约内存

    对象一旦创建，里面的数据不能改变，只要参与计算就会创建新的对象

74. BigDecimal: 不建议通过传递double来创建对象，常用传递字符串或者valueof，使用valueof时底层对0～10的整数做了优化

    对象一旦创建，里面的数据不能改变，只要参与计算就会创建新的对象

75. 查表法：让数据跟索引产生对应的关系

76. jdk8新增的时间对象都是不可变的

77. 日期时间分类（括号内为jdk7以前）

    Date类：（Date）ZoneId时区、Instant时间戳、ZoneDateTime带时区的时间

    日期格式化类：（SimpleDateFormatter）DateTimeFormmater

    日历类：（Calendar）LocalDate、LocalTime、LocalDateTime

    工具类：Duration秒纳秒、Period年月日、ChronoUnit所有时间单位

78. 在JDK5的时候提出了一个机制:自动装箱和自动拆箱
    自动装箱:把基本数据类型会自动的变成其对应的包装类
    自动拆箱:把包装类自动的变成其对象的基本数据类型

    在底层，此时还会去自动调用静态方法valueof得到一个Integer对象，只不过这个动作不需要我们自己去操作了。

    结论：在JDK5以后，int和Integer可以看做是同一个东西，因为在内部可以自动转化。

79. 以后我们如果想要键盘录入，不管什么类型，统一使用nextLine，再使用parseXxx方法转换为想要的数据类型

80. 校验时，习惯：会先把异常数据进行过滤，剩下来就是正常的数据。

81. 除基取余和按权展开

82. 函数式编程思想：忽略面向对象的复杂语法，强调做什么，而不是谁去做

83. Lambda表达式只能简化函数式接口的匿名内部类的写法

    函数式接口：有且仅有一个抽象方法的接口叫做函数式接口，接口上方可以加@Functionalnterface注解

84. Lambda省略核心：可推导，可省略

    省略规则：

    •参数类型可以省略不写。

    •如果只有一个参数，参数类型可以省略，同时(也可以省略。

    •如果Lambda表达式的方法体只有一行，大括号，分号，return可以省略不写，需要同时省略。

85. List：有序，可重复，有索引

    Set：无序，不重复，无索引

86. 迭代器遍历时，不能使用集合的方法添加或者删除。如果实在要删除，可以使用迭代器加我啊的remove方法进行删除。

87. 增强for：jdk5以后出现，为了简化迭代器的书写而出现，其底层就是一个迭代器

    只有单列集合和数组才能用增强for进行遍历

    修改增强for中的第三方变量，不会改变集合中原本的数据

88. lambda遍历：

    ```java
    coll.forEach(s -> System.out.println(s));
    ```

89. List五种遍历方式：

    需要删除元素，用迭代器

    需要增加元素，用列表迭代器

    仅仅遍历，用增强for或lambda

    需要操作索引，用普通for

90. 泛型：jdk5以后出现，编译阶段约束操作的数据类型，只能支持引用数据类型

    泛型的好处：统一数据类型；把运行时期的问题提前到了编译阶段

    为什么要使用泛型：不规定数据类型的话不能调用子类的特有方法，如果强转又会报类型转换异常

    java中的泛型是伪泛型（泛型的擦除）

    ETKV

    泛型接口：实现类可以指定类型，也可以延续泛型在创建对象时指定

    泛型不具备继承性，但是数据具备继承性

    泛型的通配符：`? extends E`和`? super E` 限定泛型的范围

91. 红黑树：

    ```
    红黑树规则：
    1. 每一个节点或是红色的,或者是黑色的
    2. 根节点必须是黑色
    3. 如果一个节点没有子节点或者父节点,则该节点相应的指针属性值为Nil,这些Nil视为叶节点,每个叶节点(Nil)是黑色的
    4. 如果某一个节点是红色,那么它的子节点必须是黑色(不能出现两个红色节点相连 的情况)
    5. 对每一个节点,从该节点到其所有后代叶节点的简单路径上,均包含相同数目的黑色节点
    ```

    ```
    红黑树添加结点：默认为红色，效率高
    - 根节点位置
      - 直接变为黑色
    - 非根节点位置
      - 父节点为黑色
        - 不需要任何操作,默认红色即可
      - 父节点为红色
        - 叔叔节点为红色
          1. 将"父节点"设为黑色,将"叔叔节点"设为黑色
          2. 将"祖父节点"设为红色
          3. 如果"祖父节点"为根节点,则将根节点再次变成黑色
          4. 如果“祖父”非根，则祖父设置为当前结点再进行判断
        - 叔叔节点为黑色，当前节点是父的左孩子
          1. 将"父节点"设为黑色
          2. 将"祖父节点"设为红色
          3. 以"祖父节点"为支点进行右旋
        - 叔叔节点为黑色，当前节点是父的右孩子
        	-把父作为当前结点并左旋，再进行判断
    ```

92. HashSet：无序，不重复，无索引

    LinkedHashSet：有序，不重复，无索引

    TreeSet：可排序，不重复，无索引

93. 哈希表底层：jdk8以前：数组+链表；jdk8开始：数组+链表+红黑树

    哈希值：对象的整数表现形式

    哈希碰撞：在小部分情况下， 不同的属性值或不同的地址值计算出来的哈希值也有可能一样

    jdk8以前：头插法；jdk8以后：尾插法

    数组的存储比例大于加载因子时，会自动扩容2倍

    jdk8以后：当链表长度超过8且数组长度大于等于64时，自动转为红黑树

    如果集合中存储的是自定义对象，必须重写equals和hashCode方法

94. TreeSet底层为红黑树，不需要重写hashCode和equals方法，但是要实现Comparable接口实现compareTo方法（默认排序）

    比较器排序：创建TreeSet对象的时候，传递比较器Comparator规则

95. 五种集合：

    集合中的元素有重复：基于数组的ArrayList（用得最多）

    集合中的元素有重复，且当前的增删操作明显多于查询：基于链表的LinkedList

    想对集合中元素去重：基于哈希表的HashSet（用得最多）

    想对集合中元素去重，且保证存取顺序：基于哈希表和双链表的LinkedHashSet

    想对集合中元素排序：基于红黑树的TreeSet

96. Map的三种遍历方式：键找值（keySet）、键值对（entrySet）、lambda表达式（forEach）

97. HashMap不需要指定排序规则，其底层的红黑树是根据哈希值的大小进行排序的

98. 三种双列集合：

    默认使用HashMap，效率最高

    如果要保证存取有序，使用LinkedHashMap

    如果要排序，使用TreeMap

99. 可变参数int...a：jdk1.5以后

    形参列表中可变参数只能有一个；可变参数必须放在形参列表的最后面

100. 对应思想：

     •如果原始数据的规律非常复杂，我们可以先手动排序让每一个数据跟唯一的序号产生对应关系。

     •序号就是数字，规律非常简单，后续的所有操作，我们以序号为准

     •当真正需要操作原始数据时候，再通过序号找到原始数据即可。

101. 不可变集合：在List、Set、Map集合中都存在静态if方法，用于获取不可变集合

     当我们要获取一个不可变的Set集合时，里面的参数一定要保证唯一性

     Map里面的of方法，参数是有上限的，最多只能传递20个参数，即10个键值对

     如果要传超过10个键值对参数，会用ofEntries方法

     ```java
     Map.ofEntries(map.entrySet().toArray(new Map.Entry[0]));
     ```

     jdk10以后，可以使用copyOf方法简化代码

     ```java
     Map.copyOf(map);
     ```

102. Stream流的获取方法：

     单列集合：Collection中的stream方法

     双列集合：调用keySet或者entrySet转换为单列集合

     数组：Arrays工具类中的静态stream方法

     一堆零散数据：Stream接口中的静态stream方法

103. Stream按口中静态方法of的细节

     方法的形参是一个可变参数，可以传递一堆零散的数据，也可以传递数组

     但是数组必须是引用数据类型的，如果传递基本数据类型，是会把整个数组当做一个元素，放到stream当中。

104. 中间方法，返回新的Stream流，原来的Stream流只能使用一次，建议使用链式编程

     修改Stream流中的数据，不会影响原来集合或者数组中的数据

105. 流的数据收集到Map集合中时，键的数据不能重复

106. 方法引用：把已经存在的方法拿过来用，当做西数式接口中抽象方法的方法体

     1.引用处需要是函数式接口

     2.被引用的方法需要已经存在

     3.被引用方法的形参和返回值需要跟抽象方法的形参和返回值保持一致

     4.被引用方法的功能需要满足当前的要求

107. 引用静态方法：`类名::静态方法`

108. 引用成员方法：`对象::成员方法`

     其他类：`其他类对象::方法名`

     本类：`this::方法名`

     父类：`super::方法名`

109. 引用构造方法：`类名::new`

110. 使用类名引用成员方法：`类名::成员方法`

     规则：被引用方法的形参，需要跟抽象方法的第二个形参到最后一个形参保持一致，返回值需要保持一致。

     局限性：不能引用所有类中的成员方法。是跟抽象方法的第一个参数有关，这个参数是什么类型的，那么就只能引用这个类中的方法。

111. 引用数组的构造方法：`数据类型[]::new`

112. Throwable子类：Error（系统级别错误）和Exception（异常）

     Exception子类：RuntimeException（运行时异常）和其他（编译时异常）

113. 编译时异常需要手动处理，用于提醒程序员检查本地信息；

     运行时异常是程序运行时出现的，一般由于参数传递错误导致

114. 异常是用来查询bug的关键参考信息

     异常可以作为方法内部的一种特殊返回值，以便通知调用者底层的执行情况

115. 处理异常的三种方式：jvm处理，捕获异常，抛出异常

116. try中产生了一个异常，try中剩下的内容都会被跳过。写多个catch的意义在于，针对这一种异常，要能够将其捕获

117. 如果我们要捕获多个异常，这些异常中如果存在父子关系的话，那么父类一定要写在下面

     在JDK7之后，我们可以在catch中同时捕获多个异常，中间用|进行隔开，表示如果出现了A异常或者B异常的话，采取同一种处理方案

118. printStackTrace()在底层是利用System.err.println进行输出，把异常的错误信息以红色字体输出在控制台，仅仅是打印信息，不会停止程序运行

119. throws：写在方法定义处，表示声明一个异常，告诉调用者，作用本方法可能会有哪些异常（编译时异常必须要写，运行时异常可以省略不写

     throw：写在方法内，结束方法，手动抛出异常对象，交给调用者，方法中下面的代码不再执行了

120. 自定义异常：定义异常类，写继承关系，空参构造，带参构造

121. File中的length方法无法获取文件夹的大小，如果要获取需要把文件夹中所有文件的大小加在一起

122. 字节输出流的细节：
         1.创建字节输出流对象
               细节1：参数是字符串表示的路径或者是File对象都是可以的
               细节2：如果文件不存在会创建一个新的文件，但是要保证父级路径是存在的。
               细节3：如果文件已经存在，则会清空文件
         2.写数据
               细节：write方法的参数是整数，但是实际上写到本地文件中的是整数在ASCII上对应的字符
         3.释放资源
               每次使用完流之后都要释放资源

123. 字节输入流的细节：
         1.创建字节输入流对象
               细节1：如果文件不存在，就直接报错。

     ​    2.写数据
     ​          细节1：一次读一个字节，读出来的是数据在ASCII上对应的数字
     ​          细节2：读到文件末尾了，read方法返回-1。

     ​    3.释放资源
     ​          细节：每次使用完流之后都要释放资源

124. 释放资源：先开的流最后关闭

125. IO流中的释放资源：

     ```java
     //基本做法：手动释放资源
     try{
       可能出现异常的代码;
     }catch(异常类名 变量名){
       异常的处理代码;
     }finally{
       执行所有资源释放操作；
     }
     ```

     ```java
     //JDK7方案：资源用完最终自动释放（必须实现了Closeable接口）
     try(创建流对象1;创建流对象2){
       可能出现异常的代码;
     }catch(异常类名 变量名){
       异常的处理代码;
     }
     ```

     ```java
     //JDK9方案：资源用完最终自动释放（必须实现了Closeable接口）
     创建流对象1;
     创建流对象2;
     try(流1;流2){
       可能出现异常的代码;
     }catch(异常类名 变量名){
       异常的处理代码;
     }
     ```

126. GBK：一个英文占一个字节，二进制第一位是0

     一个中文占两个字节，二进制高位字节的第一位是1

127. UTF-32: 固定用4个字节保存

     UTF-16:用2～4个字节保存

     UTF-8:用1～4个字节保存

128. UTF-8:不是一个字符集，它只是Unicode字符集的一种编码方式

     一个英文占一个字节，二进制第一位是0，转成十进制是正数

     一个中文占三个字节，二进制第一位是1，第一个字节转成十进制是负数

129. 乱码的原因：读取数据时末读完整个汉字；编码和解码时的方式不统一

     如何不产生乱码：不要用字节流读取文本文件；编码解码时使用同一个码表，同一个编码方式

130. ```java
     //UTF-8编码方式
     0xxxxxxx		（ASCII码）
     110xxxxx	10xxxxxx
     1110xxxx	10xxxxxx	10xxxxxx
     11110xxx	10xxxxxx	10xxxxxx	10xxxxxx
     ```

131. ```java
     //Java中编码的方法
     public byte[] getBytes()                        //使用默认方式进行编码
     public byte[] getBytes(String charsetName)      //使用指定
      //Java中解码的方法
     String(byte[] bytes)                            //使用默认方式进行解码
     String(byte[] bytes, String charsetName)        //使用指定方式进行解码
     ```

132. 字符流=字节流+字符集

     使用场景：对纯文本文件进行操作

133. 字符输入流底层原理：

     ①创建字符输入流对象

     底层：关联文件，并创建缓冲区（长度为8192的字节数组）

     ②读取数据

     底层：1.判断缓冲区中是否有数据可以读取

     2.缓冲区没有数据：就从文件中获取数据，装到缓冲区中，每次尽可能装满缓冲区

     如果文件中也没有数据了，返回-1

     3.缓冲区有数据： 就从缓冲区中读取。

     空参的read方法：一次读取一个字节，遇到中文一次读多个字节，把字节解码并转成十进制返回

     有参的read方法：把读取字节，解码，强转三步合并了，强转之后的字符放到数组中

134. 字符输出流底层原理：

     ①创建字符输入流对象

     底层：关联文件，并创建缓冲区（长度为8192的字节数组）

     ②写出数据

     三种情况下（缓冲区满、调用flush方法、调用close方法），会把缓冲区的内容写到文件中

135. 高级流：缓冲流、转换流、序列化流、打印流、压缩流

136. 字节缓冲流的读写原理：一次性读取8192个字节的数据到内存中的缓冲区，将左边的缓冲区的内容通过中间变量b或者中间数组byte[]倒腾到右边的缓冲区，当右边缓冲区满时，再写出到硬盘

137. 字符缓冲流：因为字符基本流的底层已经自带了长度为8192的缓冲区，所以提升效率不明显，但是有两个好用的特有方法
     * BufferedReader：`public String readLine()`: 读取一行数据，如果没有数据可读了，会返回null
     * BufferedWriter：`public void newLine()`: 跨平台的换行
     
138. IO流原则：随用随创建，什么时候不用什么时候关闭

139. 转换流（InputStreamReader、OutputStreamWriter）：字符流和字节流之间的桥梁

     作用1:指定字符集续写（jdk11之后淘汰，替代方案，带字符集的FileReader/FileWriter构造方法）

     作用2:字节流想使用字符流的方法

140. 序列化流（对象操作输出流ObjectOutputStream）

     序列化对象需实现Serializable接口(没有抽象方法的接口：标记型接口)

     反序列化流（对象操作输入流ObjectInputStream）

     如果要使用真正的对象类型，需要对Object进行强转

141. JavaBean在序列化中进行修改：为JavaBean添加SerialVersionUID

     transient：瞬态关键字，不会把当前属性序列化到本地文件当中

142. 将多个自定义对象序列化到文件中，但是对象个数不确定，使用ArrayList集合进行一次序列化

143. 打印流（PrintStream、PrintWriter）

     特点1：打印流只操作文件目的地，不操作数据源

     特点2：特有的写出方法可以实现，数据原样写出

     特点3：特有的写出方法，可以实现自动刷新，自动换行

144. 字节打印流底层没有缓冲区，开不开自动刷新都一样

     宇符打印流底层有缓冲区，想要自动刷新需要开启

145. System.out获取打印流的对象，此打印流在虚拟机启动的时候，由虚拟机创建，默认指向控制台

     特殊的打印流，系统中的标准输出流，是不能关闭，在系统中是唯一的。

146. 解压本质：把每一个ZipEntry按照层级拷贝到本地另一个文件夹中

147. Java 中的 `ZipEntry` 对象在处理文件时需要使用 `closeEntry` 方法来关闭当前文件的输入流，因为每个文件都是 ZIP 文件中的一个独立条目

     而对于表示文件夹的 `ZipEntry`，没有对应的数据流需要关闭，因为它们只是文件路径的一部分，并不是独立的条目

148. 使用 `BufferedWriter` 的 `newLine()` 方法会在最后一行的末尾添加一个换行符，但这并不会生成一个真正的空行。在文件中看到的空行实际上是因为最后一行末尾的换行符，它被视为最后一行的一部分。

149. 父类中的方法没有抛出异常，子类重写时也不能抛出，只能捕获

150. 并发：在同一时刻，有多个指令在单个CPU上交替执行

     并行：在同一时刻，有多个指令在多个CPU上同时执行

151. 多线程的三种启动方式：

     ```java
     //多线程的第一种启动方式：
     //编程比较简单，可以直接使用Thread类中的方法
     1．自己定义一个类继承Thread
     2．重写run方法
     3．创建子类的对象，并启动线程
     ```

     ```java
     //多线程的第二种启动方式：
     //扩展性强，实现该接口的同时可以继承其他的类
     1. 自己定义一个类实现Runnable接口
     2. 重写里面的run方法
     3. 创建自己的类的对象
     4. 创建一个Thread类的对象，并开启线程
     ```

     ```java
     //多线程的第三种实现方式：
     //特点：可以获取到多线程运行的结果
     1. 创建一个类MyCallable实现Callable接口
     2. 重写call （是有返回值的，表示多线程运行的结果）
     3. 创建MyCallable的对象（表示多线程要执行的任务）
     4. 创建FutureTask的对象（作用管理多线程运行的结果）
     5. 创建Thread类的对象，并启动（表示线程）
     ```

152. 同步代码块：

     特点1：锁默认打开，有一个线程进去了，锁自动关闭

     特点2：里面的代码全部执行完毕，线程出来，锁自动打开

     ```java
     synchronized（锁）{
     操作共享数据的代码
     }
     //锁对象，一定要是唯一的，如：
     static Object obj = new Object();
     //一般写当前类的字节码文件
     ```

153. 同步方法：

     ```java
     修饰符 synchronized 返回值类型 方法名（方法参数）{…}
     ```

     特点1：同步方法是锁住方法里面所有的代码
     特点2：锁对象不能自己指定（非静态：this；静态：当前类的字节码文件对象）

154. StringBuilder和StringBuffer两个类的内容是完全一样的，但是StringBuffer是线程安全的，它的每一个成员方法上都加上了synchronized修饰符。如果代码是单线程的，选择StringBuilder；在多线程的情况下，需要考虑数据安全时，选择StringBuffer。

155. Lock锁：JDK5以后，为了更清晰地表达获得锁和释放锁，提供了手动上锁和手动释放锁的方法

     Lock是接口不能直接实例化，这里采用它的实现类Reentrantlock来实例化

     使用同一把锁，创建lock时添加静态修饰符static

     为了保证lock一定会被释放，将lock.unlock()写在try...fanally当中

156. 为了避免死锁，在写代码时不能使用锁嵌套

157. 文件操作四步套路：

     ```java
     1.进入文件夹src
     2.遍历数组,依次得到src里面每一个文件或者文件夹
     3.判断，如果是文件，就可以执行题目的业务逻辑
     4.判断，如果是文件夹，就可以递归
     ```

158. 多线程四步套路：

     ```java
     1．循环
     2．同步代码块
     3. 判断共享数据是否到了末尾（到了末尾，跳出）
     4. 判断共享数据是否到了未尾（没有到末尾，执行核心逻辑）
     ```

159. 阻塞队列继承结构：

     接口：Iterable->Collection->Queue->BlockingQueue

     实现类：ArrayBlockingQueue和LinkedBlockingQueue

     ArrayBlockingQueue：底层是数组，有界

     LinkedBlockingQueue：底层是链表，无界，但是不是真正的无界，最大为int的最大值

160. 打印语句放在锁的外面，会造成打印混乱，但是对数据安全不造成影响

161. 线程的状态：

     ```java
     新建状态(NEW):创建线程对象
     就绪状态(RUNNABLE):start方法
     阻塞状态(BLOCKED):无法获得锁对象
     等待状态(WAITING):wait方法
     计时等待(TIMED WAITING):sleep方法
     结束状态(TERMINATED):全部代码运行完毕
     ```

     没有定义运行状态：因为线程抢夺到CPU的执行权时，JVM会把当前的线程交给操作系统管理

162. 新建对象时如果不写null，在下边调用它的方法的时候，编译过不去，提示你要实例化，这种叫编译不过；你要是写null的话，调用它下面的方法也会报错，这叫做运行时异常。

163. 线程池主要核心原理

     1. 创建一个池子，池子中是空的

     2. 提交任务时，池子会创建新的线程对象，任务执行完毕，线程归还给池子。下回再次提交任务时，不需要创建新的线程，直接复用已有的线程即可

     3. 但是如果提交任务时，池子中没有空闲线程，也无法创建新的线程，任务就会排队等待

164. 任务拒绝策略

     ```java
     ThreadPoolExecutor.AbortPolicy		//默认策略：丢弃任务并抛出RejectedExecutionException异常
     ThreadPoolExecutor.DiscardPolicy	//丢弃任务，但是不抛出异常。这是不推荐的做法
     ThreadPoolExecutor.DiscardoldestPolicy		//抛弃队列中等待最久的任务，然后把当前任务加入队列中
     ThreadPoolExecutor. CallerRunsPolicy		//调用任务的run()方法绕过线程池直接执行
     ```

     不断的提交任务，会有以下三个临界点：

     1. 当核心线程满时，再提交任务就会排队

     2. 当核心线程满，队伍满时，会创建临时线程

     3. 当核心线程满，队伍满，临时线程满时，会触发任务拒绝策略自定义线程池

165. 自定义线程池

     ```java
     核心元素一：正式员工数量										->			核心线程数量（不能小于0）
     核心元素二：餐厅最大员工数										->			线程池中最大线程的数量（最大数量 ＞=核心线程数量）
     核心元素三：临时员工空闲多长时间被辞退（值）		->			空闲时间（值）（不能小于0）
     核心元素四：临时员工空闲多长时间被辞退（单位）		->			空闲时间（单位）（用TimeUnit指定）
     核心元素五：排队的客户												->			阻塞队列（不能为null)
     核心元素六：从哪里招人												->			创建线程的方式（不能为null）
     核心元素七：当排队人数过多，超出顾客请下次再来（拒绝服务）->要执行的任务过多时的解决方案（不能为null)
     ```

     ```java
     ThreadPoolExecutor pool = new ThreadPoolExecutor(3,
             6,
             60,
             TimeUnit.SECONDS,
             new ArrayBlockingQueue<>(3),
             Executors.defaultThreadFactory(),
             new ThreadPoolExecutor.AbortPolicy()
             );
     ```

166. 最大并行数：电脑的线程数

     ```java
     int count = Runtime.getRuntime().availableProcessors();		//8
     ```

167. 线程池多大合适：

     CPU密集型（计算多，文件操作少）：最大并行数+1

     I/O密集型（大多数的项目，文件操作多，计算少）：

     ```java
     最大并行数*期望CPU利用率*总时间(CPU计算时间+等待时间)/CPU计算时间
     //从本地读取两个文件(1s)，并进行相加(1s)
     //8*100%*(2s/1s)=16
     //thread dump测试时间
     ```

168. 





---

## End





