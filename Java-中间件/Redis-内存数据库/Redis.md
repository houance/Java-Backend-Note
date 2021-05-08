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



## 事务

### MULTI

> 1. 标记事务块的开始, 此时 Redis 进入 `事务状态`
> 2. Redis 会将接下来的全部命令使用 **队列** 打包, `但不执行`, 直到看到 **EXEC**

### EXEC

> 1. Redis 看到 **EXEC**, 会执行队列中的 **全部命令**, 此时其他 **Client** `无法执行任何命令`
> 2. 执行之后 Redis 恢复 `正常连接状态`
> 3. **EXEC 不会回滚**, 即但凡 `有一条命令` 运行错误, Redis 只会`继续执行`余下的命令

### DISCARD

> 1. 清除 `所有` 放入队列的命令，然后恢复正常的 `连接状态`
> 2. 如果使用了 **WATCH** 命令，那么 **DISCARD** 命令就会将当前连接监控的所有键取消监控

### WATCH

### UNWATCH



## 持久化

### SnapShots( 数据快照-全量备份 )

+ **综述**

  > 1. **快照( SnapShots )**是指 Redis 将当前 `全部数据` 持久化到磁盘中
  > 2. **快照执行期间** 修改的数据 `不会` 被持久化到磁盘中
  > 3.  如果在 **快照执行期间** 系统崩溃, 那么在 **上一次快照完成的时候**,  到这次快照中间的数据修改`都会丢失`

+ **触发快照的方式**

  > 1. 使用 **BGSAVE** 命令
  >
  >    > 1. 此时 Redis 会 **Fork 一个子进程**进行持久
  >    > 2. `不会影响` Redis 的正常使用
  >
  > 2. 使用 **SAVE** 命令
  >
  >    > 1. 此时 Redis 会`停止运行`, 直到**持久化完成**
  >    > 2. `内存不足`时常使用此命令
  >
  > 3. 配置文件中使用 **save lines**
  >
  >    > 1. 在 Redis 的配置文件中, 可以使用 **save** 关键词配置持久化
  >    > 2. **save m n** 表示, `自从上一次 save 成功的 m 秒内有 n 个修改`发生时, 执行 **BGSAVE** 命令
  >    > 3. 可以同时使用多个 `save lines` 规则
  >
  > 4. 使用 **SHUTDOWN** 命令
  >
  >    > 1. 
  >
  > 5. 使用 **SYNC** 命令 

### AOF( Append Only File - 文件追加 )



## 其他

### 自动清除过期 Key

+ **综述**

  > 1. Redis 可以为任何 **Key** 设置一个过期时间, `到期自动删除`