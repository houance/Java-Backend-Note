# 排序

```sql
Select 列名 from 表名 ORDER BY 列名 [ASC/DESC] 默认升序;

// 如果 ORDER BY 后面跟着多个列名, 则按顺序排序
```



# 连接多个条件

```sql
Select 列名 from 表名 WHERE condition1 and/or/not;
```



## 多个 OR 条件可以使用 IN 代替

```sql
Select 列名 from 表名 WHERE 列名 in(value1, value2, value3......);
```



## 使用 () 来确定条件优先级

```sql
Select 列名 from 表名 WHERE (condition1 and/or/not condition2) and (condition3 and/or/not condition4);
```





# 判断不为空值

```sql
1. 列名 is not null;
2. 列名!='';
```



# 模糊搜索 LIKE

```sql
Select 列名 from 表名 WHERE 
列名 = a%, %a, %a% -> a开头, a结尾, 含有a
列名 = a_%, _a%, __a% -> a开头并且至少有两个字符, a在第二个位置, a在第三个位置
```



# 聚合函数

```sql
Select MIN/MAX/COUNT/AVG/SUM(列名)
from 表名 WHERE condition1;
// 返回一个值, 表示该列的 最小/最大/行数/平均值/总和
```



## Round 函数

```sql
round(value, 精度);

round(avg(列名, 1) -> 取整到一位小数;
```

