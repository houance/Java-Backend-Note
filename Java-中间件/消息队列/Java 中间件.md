# Java 中间件

[toc]

## Kafka

+ **综述**

  > `Kafka` 是一个 `分布式` 的 `流数据` 处理平台

+ **队列( Queue ) 和 广播( Pub/Sub )**

  > `Kafka` 可以实现 `队列和广播` 两种消息模式

  + **队列 ( Queue )**

    + **结构**

      <img src="Java%20%E4%B8%AD%E9%97%B4%E4%BB%B6.assets/Untitled%20Diagram%20(1)-1616042238888.png" alt="Untitled Diagram (1)" style="zoom:150%;" />

    + **讲解**

      > 1.  `Partion( 分区 )` 只能被 `一个 Consumer Group(消费者集群)` 里的 `一个 Consumer(消费者)` 消费
      > 2. 反过来 , `一个 Consumer(消费者)` 可以同时消费 `多个 Partion(分区)`

  + **广播( Pub/Sub )**

    + **结构**

      <img src="Java%20%E4%B8%AD%E9%97%B4%E4%BB%B6.assets/Untitled%20Diagram%20(2).png" alt="Untitled Diagram (2)" style="zoom:150%;" />

    + **讲解**

      > 1. `Partion(分区)` 可以被 `不同的 Consumer Group(消费者集群)` 里面的 `Consumer(消费者)` 同时消费

+ **ZooKeeper ( 未来的版本可能会移除 )**

  + **综述**

    > 1. `Zookeeper` 用于 `维护信息` , `统一命名` , `分布式同步` 和提供 `组服务(新版本中由 Kafka 自己实现了)`

  + 