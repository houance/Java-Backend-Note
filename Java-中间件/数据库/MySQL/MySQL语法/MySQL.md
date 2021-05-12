# MySQL

[toc]

## 基本语法

### SELECT/UPDATE/DELETE/INSERT INTO

+ **示例**

  + SELECT

    ```mysql
    # 选取指定列
    SELECT column1, column2, ...
    FROM table_name;
    
    # 选取全部列
    SELECT * FROM table_name;
    
    # 对指定列的全部值 进行去重
    SELECT DISTINCT column1, column2, ...
    FROM table_name;
    ```

    

  + UPDATE

    ```mysql
    # 如果没有 WHERE 语句, 会对表中 全部列 进行数据更新
    UPDATE table_name
    SET column1 = value1, column2 = value2, ...
    WHERE condition;
    ```

    

  + DELETE

    ```mysql
    # 如果没有 WHERE 语句, 会删除 整个表
    DELETE FROM table_name WHERE condition;
    ```

    

  + INSERT INTO

    ```mysql
    # 对 部分列 添加行, 剩下的列自动设置为 默认值
    INSERT INTO table_name (column1, column2, column3, ...)
    VALUES (value1, value2, value3, ...);
    
    # 对 全部列 添加行
    INSERT INTO table_name
    VALUES (value1, value2, value3, ...);
    ```

    

### WHERE

+ **综述**

  > 1. 用于从 **结果集** 中筛选 `符合条件` 的数据
  > 2. 可以使用 `AND, OR, NOT` 关键字 **连接** 多个条件 

+ **示例**

  ```mysql
  # AND, OR 用于连接多个条件
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition1 AND / OR condition2 AND / OR condition3 ...;
  
  # NOT 用于展示 不符合条件 的数据
  SELECT column1, column2, ...
  FROM table_name
  WHERE NOT condition;
  ```

### ORDER BY

+ **综述**

  > 1. 对 **结果集** 排序, 默认是 `升序`

+ **示例**

  ```mysql
  SELECT column1, column2, ...
  FROM table_name
  ORDER BY column1, column2, ... ASC|DESC;
  ```

### LIMIT

+ **综述**

  > 1. 用于从 **结果集** 中返回指定数量的结果
  > 2. 可以提高性能

+ **示例**

  ```mysql
  SELECT column_name(s)
  FROM table_name
  WHERE condition
  LIMIT number;
  ```

  

### LIKE



## 常用技巧

+ **去重**

  ```mysql
  SELECT DISTINCT 需要去重的字段名 ......;
  
  GROUP BY 需要去重的字段名 ......;
  ```

+ **子查询**

  ```mysql
  # 用于 在另一个查询语句 的结果里面查询
  WHERE 字段名 NOT IN/IN (SELECT ......);
  ```

+ **判断字段值是否为 NULL**

  ```mysql
  WHERE 字段名 IS NULL/NOT NULL;
  ```

  

## 分组( GROUP BY )

+ **综述**

  > 1. 根据 **一个或多个字段** 进行 `分组`, 常配合 **聚合函数** 使用
  >
  > 2. 对 **一个字段** 进行分组
  >
  >    > 1. 此时会对该 **字段列** 的所有值 `进行排序`
  >    > 2. 然后把该字段列 `具有相同值` 的**多条记录合并为一组记录**
  >    > 3. 对于 **被组合** 的行, 此时如果调用 `SELECT` , 只会显示每个字段的`第一个值`
  >
  >    ![Untitled Diagram](MySQL.assets/Untitled%20Diagram-1620709978133.png)
  >
  > 3. 对 **多个字段** 进行分组
  >
  >    > 1. 此时会对 **多个字段列** 的所有值 `进行排序`
  >    > 2. 只有 **多个字段值** `完全相同的` 的记录才会被 `归为一组`
  >    > 3. 对于 **被组合** 的行, 此时如果调用 `SELECT` , 只会显示每个字段的`第一个值`
  >
  >    ![Untitled Diagram (1)](MySQL.assets/Untitled%20Diagram%20(1)-1620709987142.png)

+ **语法**

  ```mysql
  SELECT 字段名, function() as 变量名
  FROM 表名
  [WHERE column_name operator value]
  GROUP BY 字段名,字段名
  []having 条件(变量名 >/</=)];
  ```

  

## 聚合函数

### COUNT / 计数

+ **综述**

  > 1. 用于统计 **符合条件** 的 `行数`

+ **语法**

  > 1. count(*)
  >
  >    > 统计整个表的 `全部行数` , 不会忽略`存在值为 NULL` 的行
  >
  > 2. count( 字段名 )
  >
  >    > 统计 **指定字段列** 的行数, 忽略 `值为 NULL ` 的行
  >
  > 3. count( distinct 字段名 )



## 连接查询

### 交叉连接( Cross Join )



### 内连接( Inner Join )

+ **示意图**

  ![Screenshot from 2021-05-10 22-47-44](MySQL.assets/Screenshot%20from%202021-05-10%2022-47-44.png)

+ **综述**

  > 1. 查找 **两张表** 之间 `字段值一样` 的 行记录

+ **语法**

  ```mysql
  # SELECT 决定了数据 拼接展示 的顺序
  SELECT 表名.字段名, 表名.字段名
  # FROM 表示从内连接之后的表查询
  # on 表示内连接的条件
  FROM 表名 inner join 表名 on 表名.字段名=表名.字段名
  ```

  

### 左外连接( Left Outer Join )

+ **示意图**

  ![Screenshot from 2021-05-10 22-47-52](MySQL.assets/Screenshot%20from%202021-05-10%2022-47-52.png)

+ **综述**

  > 1. 查找 **两张表** 之间 `字段值一样` 的 行记录
  > 2. **如果没有**, 则展示 `左表` 的 行记录, 且属于 `右表` 的行记录值为 `NULL`

+ **语法**

  ```mysql
  # SELECT 决定了数据 拼接展示 的顺序
  SELECT 表名.字段名, 表名.字段名
  # FROM 表示从内连接之后的表查询
  # on 表示内连接的条件
  FROM 表名 inner join 表名 on 表名.字段名=表名.字段名
  ```

  

### 右外连接( Right Outer Join)