# kafka

#### Kafka如何保证消息可靠性和一致性 [https://codeantenna.com/a/slGqbd6gBh](https://codeantenna.com/a/slGqbd6gBh)

* 生产者数据的不丢失 ACK
* 保存的数据不丢失(ISR HW)
* 消费者数据的不丢失 （OFFSET）

#### 聊一聊kafka再均衡rebalance [https://blog.csdn.net/yidan7063/article/details/108234222](https://blog.csdn.net/yidan7063/article/details/108234222)

* 再均衡（ Rebalance ）本质上是一种协议，规定了一个消费组中所有消费者如何达成一致来分配订阅主题的每个分区。 比如某个消费组有 20 个消费组，订阅了一个具有 100 个分区的主题。正常情况下， Kafka 平均会为每个消费者分配5 个分区。这个分配的过程就叫再均衡。
* Kafka 提供了一个角色： Group Coordinator来执行对于消费组的管理。
* 再均衡的触发条件：1.组成员发生变更  2.订阅主题数发生变更 3.订阅主题的分区数发生变更

#### 幂等性 [https://www.jianshu.com/p/b1599f46229b](https://www.jianshu.com/p/b1599f46229b)

* 幂等是针对生产者角度的特性。幂等可以保证上生产者发送的消息，不会丢失，而且不会重复
* 为了实现Producer的幂等性，Kafka引入了Producer ID（即PID）和Sequence Number。

#### kafka高性能[https://juejin.cn/post/6986572136588509214](https://juejin.cn/post/6986572136588509214)

* 零拷贝 (mmap  sendfile) 直接从磁盘文件复制到网卡设备中，而不需要经由应用程序之手顺序写
* 顺序读写
* Page Cache
* 批量操作
* 数据压缩
* 日志分段存储
