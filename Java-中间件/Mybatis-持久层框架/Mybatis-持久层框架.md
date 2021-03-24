# Mybatis-ORM-持久层框架 

[toc]

## 1.什么是 Persistence ( 持久层 )

> 1. `Persistence` 是指将 `数据` 存储起来( 一般存到 磁盘 或者数据库 ), 以便再次使用.

## 2. 什么是 JDBC( Java-Database-Connectity )

+ **综述**

  > 1. `JDBC` 是 Java 连接数据库的一套底层 `API` ,解决了使用编程语言控制数据库的问题.
  > 2. 但是 `JDBC` 仅仅提供 `最原始的连接数据库` 的方法, 在使用的时候需要写 `SQL` 语句, 并且做各种`异常处理` , 也缺乏 `面向对象` 的方法, 非常繁琐.

+ **JDBC 代码示例**

  

## 3. 什么是 ORM ( Object-Realation-Mapping)

+ **Object 储存数据的方式**

  <img src="Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/Copy%20of%20realtime-cv-api-platform%20(2).png" alt="Copy of realtime-cv-api-platform (2)" style="zoom:150%;" />

  <img src="Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/Copy%20of%20realtime-cv-api-platform%20(4).png" alt="Copy of realtime-cv-api-platform (4)" style="zoom:150%;" />

  > 1. 任何 `面向对象( Object Oriented )` 编程的语言, 都使用类似的方式储存数据

+ **Realation Database 储存数据的方式**

  <img src="Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/job%20table.png" alt="job table" style="zoom:150%;" />

  <img src="Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/Copy%20of%20Copy%20of%20realtime-cv-api-platform.png" alt="Copy of Copy of realtime-cv-api-platform" style="zoom:150%;" />

  > 1. `关系数据库 ( Realation-DB )` 则使用类似表格的方式储存数据.
  > 2. `添加和查询` 都是以 `行` 为基本单位

+ **ORM ( Object-Realation-Mapping)**

  <img src="Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/orm.png" alt="orm" style="zoom:150%;" />

  > 1. `ORM( Object-Realation-Mapping )` 就是为了解决 `OO( Object-Oriented )` 编程语言与 `Realation-DB` 之间交互存在的问题
  > 2. 问题举例 : `数据类型转换( bigint--Long, varchar--string )`, `复杂的查询动作( Join, Merge ...... )`, 对象之间的依赖关系与 `表的映射 ( Mapping ) `等等

## 4. Mybatis vs Hibernate/JPA

+ **Mybatis**

  ![Screenshot from 2021-03-25 00-15-54](Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/Screenshot%20from%202021-03-25%2000-15-54.png)

  + **综述**

    > 1. `Mybatis` 是一款 `ORM + Persistence` 框架
    > 2. 需要用户自己写 `SQL`, 可以自己优化 `SQL`, 最大化性能
    > 3. 底层封装了 `JDBC`, 省去了 `连接数据库, 转换参数, 异常检查` 等繁琐语句.
    > 4. 拥有数据库`连接池`, 减小数据库连接开销
    > 5. 自带`缓存机制`, 可以将之前查询的结果`存储在内存`

+ **什么是 Hibernate/JPA**

  ![Screenshot from 2021-03-25 00-16-02](Mybatis-%E6%8C%81%E4%B9%85%E5%B1%82%E6%A1%86%E6%9E%B6.assets/Screenshot%20from%202021-03-25%2000-16-02.png)

  + **综述**

    > 1. `Hibernate` 是一款 `ORM + Persistence` 框架
    > 2. 不需要用户自己写 `SQL` ,全部操作都通过 `OO` 的方式
    > 3. 符合 `JPA( Java Persistence API )` 规范, 即用户可以随时使用其他符合 `JPA` 的框架, 不需要更改代码.

## 5. 使用 Mybatis



