## DDL数据定义语言

### 1.查询数据库

**查询所有数据库：**

```mysql
show databases;
```

**查询当前数据库：**

```mysql
select database();
```



### 2.创建数据库

```mysql
create database [ if not exists ] 数据库名;
```



### 3.创建数据库

```mysql
use 数据库名 ;
```



### 4.删除数据库

```mysql
drop database [ if exists ] 数据库名 ;
```



### 5.表创建

```mysql
create table  表名(
	字段1  字段1类型 [约束]  [comment  字段1注释 ],
	字段2  字段2类型 [约束]  [comment  字段2注释 ],
	......
	字段n  字段n类型 [约束]  [comment  字段n注释 ] 
) [ comment  表注释 ] ;
```

*非空约束：not null*

*唯一约束：unique*

*主键约束：primary key*

*默认约束：default*

*外键约束：foreign key*



### 6.表查询

**查询当前数据库所有表**

```mysql
show tables;
```

**查看指定表结构**

```mysql
desc 表名 ;#可以查看指定表的字段、字段的类型、是否可以为NULL、是否存在默认值等信息
```

**查询指定表的建表语句**

```mysql
show create table 表名 ;
```



### 7.表修改

**添加字段**

```mysql
alter table 表名 add  字段名  类型(长度)  [comment 注释]  [约束];
```

**修改数据类型**

```mysql
alter table 表名 modify  字段名  新数据类型(长度);
```

```mysql
alter table 表名 change  旧字段名  新字段名  类型(长度)  [comment 注释]  [约束];
```

**删除字段**

```mysql
alter table 表名 drop 字段名;
```

**修改表名**

```mysql
rename table 表名 to  新表名;
```



### 8.表删除

```mysql
drop  table [ if exists ]  表名;
```

---

## DML数据操作语言

### 1.添加数据

**向指定字段添加数据**

```mysql
insert into 表名 (字段名1, 字段名2) values (值1, 值2);
```

**全部字段添加数据**

```mysql
insert into 表名 values (值1, 值2, ...);
```

**批量添加数据（指定字段）**

```mysql
insert into 表名 (字段名1, 字段名2) values (值1, 值2), (值1, 值2);
```

**批量添加数据（全部字段）**

```mysql
insert into 表名 values (值1, 值2, ...), (值1, 值2, ...);
```



### 2.修改数据

```mysql
update 表名 set 字段名1 = 值1 , 字段名2 = 值2 , .... [where 条件] ;
```



### 3.删除数据

```mysql
delete from 表名  [where  条件] ;
```

*DELETE 语句不能删除某一个字段的值(可以使用UPDATE，将该字段值置为NULL即可)。*

---

## DQL数据查询语言

```mysql
SELECT
	字段列表
FROM
	表名列表
WHERE
	条件列表
GROUP  BY
	分组字段列表
HAVING
	分组后条件列表
ORDER BY
	排序字段列表
LIMIT
	分页参数
```

### 1.基本查询

**查询多个字段**

```mysql
select 字段1, 字段2, 字段3 from  表名;
```

**查询所有字段（通配符）**

```myslq
select *  from  表名;
```

*`*`号代表查询所有字段，在实际开发中尽量少用（不直观、影响效率）*

**设置别名**

```mysql
select 字段1 [ as 别名1 ] , 字段2 [ as 别名2 ]  from  表名;
```

*as可以省略*

*别名中有特殊字符时，使用''或""包含*

**去除重复记录**

```mysql
select distinct 字段列表 from  表名;
```

### 2.条件查询

```mysql
select  字段列表  from   表名   where   条件列表 ; -- 条件列表：意味着可以有多个条件
```

- 比较运算符

*`>`、`>=`、`<`、`<=`、`=`、`<>或者!=`*

*`between ...  and ... `在某个范围之内(含最小、最大值)*

*`in(...)` 在in之后的列表中的值，多选一*

*`like 占位符` 模糊匹配(_匹配单个字符, %匹配任意个字符)*

*`is null `是null*

- 逻辑运算符

*`and或者&&`、`or或者||`、`not或者!`*



### 3.聚合函数

```mysql
select  聚合函数(字段列表)  from  表名 ;
```

 *聚合函数会忽略空值，对NULL值不作为统计。*

*count ：按照列去统计有多少行数据。*

- *在根据指定的列统计的时候，如果这一列中有null的行，该行不会被统计在其中。*
- *count(字段)、count(常量)、count(*)  推荐此写法（MySQL底层进行了优化）*

*sum ：计算指定列的数值和，如果不是数值类型，那么计算结果为0*

*max ：计算指定列的最大值*

*min ：计算指定列的最小值*

*avg ：计算指定列的平均值*



### 4.分组查询

```mysql
select  字段列表  from  表名  [where 条件]  group by 分组字段名  [having 分组后过滤条件];
```

*分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义*

*执行顺序：where > 聚合函数 > having* 

条件表达式：`if(条件表达式, true取值 , false取值)`，如：

```mysql
select if(gender=1,'男性员工','女性员工') AS 性别, count(*) AS 人数
from tb_emp
group by gender;
```

`case 表达式 when 值1 then 结果1  when 值2  then  结果2 ...  else  result  end`

```mysql
select (case job
             when 1 then '班主任'
             when 2 then '讲师'
             when 3 then '学工主管'
             when 4 then '教研主管'
             else '未分配职位'
        end) AS 职位 ,
       count(*) AS 人数
from tb_emp
group by job;
```



### 5.排序查询

```mysql
select  字段列表  
from   表名   
[where  条件列表] 
[group by  分组字段 ] 
order  by  字段1  排序方式1 , 字段2  排序方式2 … ;
```

*排序方式：升序asc（默认值）；降序desc*

*如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序* 



### 6.分页查询

```mysql
select  字段列表  from   表名  limit  起始索引, 查询记录数 ;
```

*如果查询的是第1页数据，起始索引可以省略，直接简写为：limit 条数*

*分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT*



### 7.外键约束

**创建表时指定**

```mysql
create table 表名(
	字段名    数据类型,
	...
	[constraint]   [外键名称]  foreign  key (外键字段名)   references   主表 (主表列名)	
);
```

**建完表后，添加外键**

```mysql
alter table  表名  add constraint  外键名称  foreign key(外键字段名) references 主表(主表列名);
```

*物理外键：影响增、删、改的效率（需要检查外键关系）；仅用于单节点数据库，不适用与分布式、集群场景；容易引发数据库的死锁问题，消耗性能。*

*在现在的企业开发中，很少会使用物理外键，都是使用逻辑外键（在业务层逻辑中，解决外键关联。）*



### 8.多表：连接查询

**隐式内连接**

```mysql
select  字段列表   from   表1 , 表2   where  条件 ... ;
```

**显式内连接**

```mysql
select  字段列表   from   表1  [ inner ]  join 表2  on  连接条件 ... ;
```

**左外连接**

```mysql
select  字段列表   from   表1  left  [ outer ]  join 表2  on  连接条件 ... ;
```

**右外连接**

```mysql
select  字段列表   from   表1  right  [ outer ]  join 表2  on  连接条件 ... ;
```

*左外连接和右外连接是可以相互替换的，只需要调整连接查询时SQL语句中表的先后顺序就可以了。而我们在日常开发使用时，更偏向于左外连接。*



### 9.多表：子查询

```mysql
SELECT  *  FROM   t1   WHERE  column1 =  ( SELECT  column1  FROM  t2 ... );
```

**标量子查询**

```mysql
-- 1.查询"教研部"部门ID
select id from tb_dept where name = '教研部';    #查询结果：2
-- 2.根据"教研部"部门ID, 查询员工信息
select * from tb_emp where dept_id = 2;

-- 查询"教研部"的所有员工信息
select * from tb_emp where dept_id = (select id from tb_dept where name = '教研部');
```

**列子查询**

```mysql
-- 1.查询"销售部"和"市场部"的部门ID
select id from tb_dept where name = '教研部' or name = '咨询部';    #查询结果：3,2
-- 2.根据部门ID, 查询员工信息
select * from tb_emp where dept_id in (3,2);

-- 查询"教研部"和"咨询部"的所有员工信息
select * from tb_emp where dept_id in (select id from tb_dept where name = '教研部' or name = '咨询部');
```

**行子查询**

```mysql
-- 查询"韦一笑"的入职日期 及 职位
select entrydate , job from tb_emp where name = '韦一笑';  #查询结果： 2007-01-01 , 2
-- 查询与"韦一笑"的入职日期及职位相同的员工信息
select * from tb_emp where (entrydate,job) = ('2007-01-01',2);

-- 查询与"韦一笑"的入职日期及职位都相同的员工信息 
select * from tb_emp where (entrydate,job) = (select entrydate , job from tb_emp where name = '韦一笑');
```

**表子查询**

```mysql
-- 查询入职日期是 "2006-01-01" 之后的员工信息
select * from emp where entrydate > '2006-01-01';

-- 基于查询到的员工信息，在查询对应的部门信息
select e.*, d.* from (select * from emp where entrydate > '2006-01-01') e left join dept d on e.dept_id = d.id ;
```

---

## 事务控制

**开启手动控制事务**

```mysql
start transaction;  /  begin ;
```

**提交事务**

```mysql
commit;
```

**回滚事务**

```mysql
rollback;
```

事务的四大特性：

- 原子性（Atomicity）：事务是不可分割的最小单元，要么全部成功，要么全部失败。
- 一致性（Consistency）：事务完成时，必须使所有的数据都保持一致状态。
- 隔离性（Isolation）：数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行。
- 持久性（Durability）：事务一旦提交或回滚，它对数据库中的数据的改变就是永久的。

---

## 索引

创建索引

```mysql
create  [ unique ]  index 索引名 on  表名 (字段名,... ) ;
```

查看索引

```mysql
show  index  from  表名;
```

**删除索引**

```mysql
drop  index  索引名  on  表名;
```

---

## Contact 字符串拼接函数

```mysql
concat('%' , '关键字' , '%')
```

---

## MyBatis动态SQL

`<if>`

用于判断条件是否成立。使用test属性进行条件判断，如果条件为true，则拼接SQL。

```xml
<if test="条件表达式">
   要拼接的sql语句
</if>
```

`<where>`

只会在子元素有内容的情况下才插入where子句，而且会自动去除子句的开头的AND或OR

```xml
<select id="list" resultType="com.itheima.pojo.Emp">
        select * from emp
        where
    
             <if test="name != null">
                 name like concat('%',#{name},'%')
             </if>
             <if test="gender != null">
                 and gender = #{gender}
             </if>
             <if test="begin != null and end != null">
                 and entrydate between #{begin} and #{end}
             </if>
    
        order by update_time desc
</select>
```

`<set>`

动态的在SQL语句中插入set关键字，并会删掉额外的逗号。（用于update语句中）

`<forEach>`

```xml
<foreach collection="集合名称" item="集合遍历出来的元素/项" separator="每一次遍历使用的分隔符" 
         open="遍历开始前拼接的片段" close="遍历结束后拼接的片段">
</foreach>
```

`<sql>`

定义可重用的SQL片段

```xml
<sql id="commonSelect">
 	select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, update_time from emp
</sql>
```

`<include>`

通过属性refid，指定包含的SQL片段

```xml
<include refid="commonSelect"/>
```

