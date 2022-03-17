《MySql的相关操作》

## 前沿 数据库相关

- 数据库：数据库是一些**关联表**的集合
- 数据表：表是数据的矩阵。一个数据库中的表看起来就像是一个简单的电子表格
- 列：一列(数据元素)包含了**相同类型**的数据
- 行：一行(记录)是一组相关的数据
- 冗余：存储两倍的数据，冗余降低了性能，但提高了数据的安全性
- 主键：``primary key`` ，主键是唯一的，一个数据表中只能有一个主键，特殊的是联合主键
- 外键：``foreign key``，外键用于关联两个表
- 复合键：又称组合键，将多个列作为一个索引键，一般用于复合索引
- 索引：使用索引可快速访问数据表中的特定信息，索引是对数据库表中一列或多列的值进行排序的一种结构。
- 参照完整性：参照的完整性要求关系中不允许引用不存在的实体，与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性。

### 0 mysql中的注释

```mysql
-- show databases;  
/*show databases;*/
```

### 1查看mysql数据库中成存在哪些数据库？

```mysql
show databases;
```

### 2 创建自己的数据库：create

```mysql
create database abc;
```

### 3 创建数据库并指定字符集:charset

```mysql
create database abc charset=utf8;     /* 一个汉字三个字节*/
create database abc charset=utf8mb4;    /*一个汉字四个字节，类似于``utf16``*/
```

### 4 选择使用指定的数据库:use

```mysql
create database abc charset=utf8;  /* 没有想要的数据库时，先创建*/
use abc;   
```

### 5 删除数据库:drop

```mysql
 drop database abc;
```

### 6 mysql数据库中的表:关系型数据库

```mysql
-- 表是建立在数据库中的数据结构，是一类数据的存储集
```

### 7 在指定数据库下创建表：create table

```mysql
create database abc charset=utf8;  /* 没有想要的数据库时，先创建*/
use abc;   
create table name (id int primary key auto_increment,name varchar(20),age int, location varchar(20)) charset=utf8 engine=innodb;
/*
id  name  age  location是字段名
 primary key表示主键
 auto_increment表示自动增长
int varchar是数据类型，数字20表示最大长度
charset 是设置字符集，字符集如果不指定，默认继承库的字符集
engine是表的存储引擎，默认是innodb，还有一个重要的存储引擎是myisam
*/
```

### 8 查询所有的表：show tables

```mysql
create database abc charset=utf8;  /* 没有想要的数据库时，先创建*/
use abc;   
-- 创建了3个表
create table name (id int primary key auto_increment,name varchar(20),age int, location varchar(20)) charset=utf8 engine=innodb;
create table name1 (id int primary key auto_increment,name varchar(20),age int, location varchar(20)) charset=utf8 engine=innodb;
create table name2 (id int primary key auto_increment,name varchar(20),age int, location varchar(20)) charset=utf8 engine=innodb;

# 查看所有的表
show tables;  -- name name1 name2
```

### 9 查看表的结构：desc 

```mysql
-- 查看name表的结构
desc name;
describe name;
```

### 10 向表中插入数据：insert into

```mysql
-- 首先查看name表的结构，再进行数据的插入，防止列不匹配
desc name;
insert into name values (1,"hello",20,"Chinese");  -- 插入一个数据
insert into name values (2,'张三',28,'FRI'),(3,'jack',30,'JP'); -- 插入多行数据

-- 只向表中的某些字段插入数据
insert into name (name,age) values ('jerry',20),('sunny',23);
```

### 11 查看表中的数据

```mysql
-- * 表示查询表中的所有字段
select * from name;

--如果只是想查询出表中的某些字段
select id,name from name;
--结果就是只显示出id,name的字段的信息
```

