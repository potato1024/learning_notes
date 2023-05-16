## IDEA mac 快捷键

- 格式化代码：==cmd+opt+L==
- 多行注释：==cmd+opt+/==或者==cmd+shift+/==
- 查看参数调用情况：==cmd+p==
- 抽取代码为方法：==cmd+opt+m==
- 批量修改变量名：==shift+f6==
- 对象接收：==cmd+opt+v==或者==.var==
- 包裹代码块：==cmd+opt+t==
- 全局查找（nevigate）：==shift+shift==
- 自动生成getset方法：==cmd+n==或者==ctrl+enter==
- 向下复制一行：==cmd+d==
- 竖排选中：==opt不松==
- 类找方法：==cmd+f12==
- 跟进：==cmd+b==
- 接口的实现类：==cmd+opt+b==
- 返回：==cmd+opt+左==或者==cmd+[==
- 变量切割：==opt+enter==
- 整行移动：==shift+opt+上下==
- 撤销：==cmd+shift+z==
- run：==ctrl+shift+r==
- debug：==ctrl+shift+d==
-  重写方法：==ctrl+o==

---

## IDEA 代码模板

- 主函数：==psvm、main==
- 输出语句：==sout==
- 输出占位语句：==souf（使用%s占位）==
- 循环：==fori==
- 倒序遍历：==forr==
- 对象接收：==var==

---

## String类常用方法

- 提取字符：==chatAt==
- 分割字符：==substring==
- 替换：==replace==
- 生成字符数组：==tochararray==
- 忽略大小写的比较：==equalsIgnoreCase==

### StringBuilder类

- 添加：==append==
- 反转：==reverse==

### Stringjoiner类

- 构造：==new Stringjoiner("---")==或者==new Stringjoiner(", ", "[","]" )==
- 添加：==add==

---

## 概念

- 字面量
- JavaBean（插件：PTG）

---

## Tips

0. ```java
   Scanner sc = new Scanner(System.in);
   int num = sc.nextInt();
   //第一套体系：next（），nextInt（），nextDouble（）在接收数据的时候，会遇到空格，回车，制表符其中一个就会停止接收数据。
   //第二套体系：nextLine（）方法是把一整行全部接收完毕。
   Random r = new Random();
   int num = r.nextInt(10);
   
   ```

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
   >     case 1, 2, 3, 4, 5 -> System.out.println("工作日");
   >     case 6, 7 -> System.out.println("休息日");
   >     default -> System.out.println("没有这个星期");
   > }

​		对switch的结果整体赋值：

> String str =switch(){
>
> case’-’ ->””
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

14. String str = "abc"

    等效于String str = new String(chs);
    
    

