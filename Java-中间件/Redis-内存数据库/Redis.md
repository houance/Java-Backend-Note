# Redis



## 综述

> 1. 数据以 `键值对` 的形式存储在 `内存` 中, 同时也支持 `持久化到磁盘`中
> 2. **键( Key )** 是 `string` 类型, **值( Value )** 可以是`任何`数据类型
> 3. 通常情况下是 **单线程**, 持久化时是 **多线程**
> 4. 交互方式类似于 `HTTP`, 即以 **Request/Response** 的形式交互, 传输协议是 **TCP**

## 数据结构

### Strings

+ **示意图**

  ![Screenshot from 2021-05-07 23-07-34](Redis.assets/Screenshot%20from%202021-05-07%2023-07-34.png)

+ **综述**

  > 1. **值( Value )** 是 `字符串, 整型, 浮点型` 数据类型
  >
  > 2. 支持操作
  >
  >    > 1. 

### Lists

+ **示意图**

  ![Screenshot from 2021-05-07 23-13-29](Redis.assets/Screenshot%20from%202021-05-07%2023-13-29.png)

+ **综述**

  > 1. **值( Value )** 是任意数量的 `string`, 类似 **双端链表**
  >
  > 2. 元素**可以重复**, 存储**有序**
  >
  > 3. 支持操作
  >
  >    > 1. 从 `左/右 端 存储/取出` 数据 --  L/RPUSH, L/RPOP 
  >    > 2. 任意访问( Random Access ) -- LINDEX
  >    > 3. 块访问 -- LRANGE
  >    > 4. 裁剪大小 -- LTRIM

### Sets

+ **示意图**

  ![Screenshot from 2021-05-07 23-24-15](Redis.assets/Screenshot%20from%202021-05-07%2023-24-15.png)

+ **综述**

  > 1. **值( Value )** 是任意数量的 `string`
  >
  > 2. 元素**不可以重复**, 存储的**顺序未知**
  >
  > 3. 支持操作
  >
  >    > 1. 增, 删, 查 -- SADD, SREM, SMEMBERS
  >    > 2. 集合操作 -- SDIFF, SINTER, SUNION

### Hashes

+ **示意图**

  ![Screenshot from 2021-05-07 23-48-37](Redis.assets/Screenshot%20from%202021-05-07%2023-48-37.png)

+ **综述**

  > 1. **值( Value )** 是任意数量的 `Strings`
  >
  > 2. 元素的 **键不可以重复**, 存储的**顺序未知**
  >
  > 3. 支持操作
  >
  >    > 1. 增, 删, 查 -- HMSET, HDEL, HGET
  >    > 2. 查键, 遍历键/值, 遍历 -- HEXISTS, HKEYS/HVALS, HGETALL

### Sorted Sets/ZSets

+ **示意图**

  ![Screenshot from 2021-05-08 00-15-40](Redis.assets/Screenshot%20from%202021-05-08%2000-15-40.png)

+ **综述**

  > 1. **值( Value )** 是任意数量的 `Member-Score`
  >
  >    > 1. 类似 **Key-Value** 的数据结构
  >    > 2. Member 是 **字符串**, 而 Score 是 **浮点数**
  >
  > 2. 元素的 **Member 不可以重复**, 按照 **Score 的大小** 排序
  >
  > 3. 支持操作
  >
  >    > 1. 增, 删, 查 -- ZADD, ZREM, ZRANGE