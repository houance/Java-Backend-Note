# 综述

*Consul 是一个开源的, 轻量级的 **服务治理** 组件*

> 服务治理 = 服务发现 + 服务分割( Segmentation ) + 配置中心



# [拓展] Gossip 算法

<video src="C:/Users/83750/Desktop/gossip.mp4"></video>



*Gossip 过程是由种子节点发起，当一个种子节点有状态需要更新到网络中的其他节点时，它会随机的选择周围几个节点散播消息，收到消息的节点也会重复该过程，直至最终网络中所有的节点都收到了消息。这个过程可能需要一定的时间，由于不能保证某个时刻所有节点都收到消息，但是理论上最终所有节点都会收到消息，因此它是一个最终一致性协议。*

> 1. 使用 Gossip 的好处是异步, 你不需要给每一个结点发送消息
> 2. 坏处就是信息的延迟, 冗余



# 架构

<img src="Consul.assets/consul-arch.png" alt="Consul Architecture" style="zoom: 33%;" />

1. 每个 DC ( Datacenter ) 存储的数据都是 **不一样** 的
2. 在一个 DC 内, 分为 Server 和 Client 两种结点, **Server** 数量为 3~5 个,  **Client** 数量不限制



# Agent

1. **Server** 和 **Client** 统称为 *Agent*

2. **Server** 负责 *存储信息, 容灾 和 Leader 选举( 使用 Raft 算法 )*

   > 1. 系统会维护一个 Server Gossip Pool. 负责发起 Gossip 算法 和 跨数据中心交互
   > 2. Leader Server 负责处理 **全部请求 和 事务**

3. **Client** 负责 *服务注册, 健康检查*

   > 1. 一般来说, Client 部署在提供服务的机器上, 属于轻量级进程
   > 2. 系统也会维护一个 Client Gossip Pool. 负责发起 Gossip 算法

4. 请求可以发到任何一个 Agent, 每一个 Agent 都会自动将请求转发到目标 Server, 甚至是跨数据中心的 Server





# 数据中心 ( Datacenter )

1. 每个数据中心存储的消息都是不一样的