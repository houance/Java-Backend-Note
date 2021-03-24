# Mybatis-ORM-持久层框架 

[toc]



## 1. 什么是 JDBC( Java-Database-Connectity )

+ **综述**

  > 1. `JDBC` 是 Java 连接数据库的一套底层 `API` ,解决了使用编程语言控制数据库的问题.
  > 2. 但是 `JDBC` 仅仅提供 `最原始的连接数据库` 的方法, 在使用的时候需要写 `SQL` 语句, 并且做各种`异常处理` , 也缺乏 `面向对象` 的方法, 非常繁琐.

+ **JDBC 代码示例**

  

## 2. 什么是 ORM ( Object-Realation-Mapping)

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
  > 3. 底层是对 `JDBC` 的封装, 提供了完备的 `ORM` 方法, 简化的数据库的使用.

## 3. 什么是 Mybatis 

## 4. 什么是 Hibernate 和 JPA

## 5. Mybatis vs Hibernate

## 6. 使用 Mybatis



