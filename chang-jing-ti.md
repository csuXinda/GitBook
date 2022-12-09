# 场景题

#### 高并发设计经验（[https://mp.weixin.qq.com/s/PPQzMOZ\_1t19hFdTO60xKA](https://mp.weixin.qq.com/s/PPQzMOZ\_1t19hFdTO60xKA)）

#### 秒杀系统（[https://www.cnblogs.com/chanshuyi/p/how-to-design-a-second-killing-system.html](https://www.cnblogs.com/chanshuyi/p/how-to-design-a-second-killing-system.html)）

* 前端（**页面静态化 + CDN」、请求频率限制进行优化**）
* 后端（**一般有「增加缓存层 + 预热数据」、「MQ 异步处理」、「限流、熔断、降级」、业务侧优化这 4 种优化方式。**）

#### 设计RPC

#### 短链接

#### 排行榜

#### 微信抢红包（[https://www.infoq.cn/article/2017hongbao-weixin](https://www.infoq.cn/article/2017hongbao-weixin)）

* 对比分析：方案一：内存代替db操作，可以提高并发能力，但是可能出现数据丢失情况，不适用于资金交易系统；方案二：db乐观锁代替悲观锁，事物回滚和并发大小会影响用户体验
* SET 化、请求排队串行化、memcached cas控制并发，维度分库



#### 设计点赞功能

#### 微博feed流、朋友圈

#### 定时任务

#### 分布式id、锁、事务（[https://www.cnblogs.com/chengxy-nds/p/12315917.html](https://www.cnblogs.com/chengxy-nds/p/12315917.html)）（）

* 雪花算法 毫秒时间戳+机器id+自增id
* redis增长incre命令
* 数据库自增长id，集群按区间区分启始位置，但是不利于扩容，
* 数据库号段模式，获取自增ID，号段可以理解成批量获取，比如`DistributIdService`从数据库获取ID时，如果能批量获取多个ID并缓存在本地的话，那样将大大提供业务应用获取ID的效率。

分布式事务（[https://xiaomi-info.github.io/2020/01/02/distributed-transaction/](https://xiaomi-info.github.io/2020/01/02/distributed-transaction/)）

* 理论2PC协调者
* 理论TCC
* 理论本地事件-生产者消费
* 尽最大努力通知-(轮询)
* 可靠消息最终一致性
* rocketmq事务

#### 各种海量数据处理

* 分治归并
* top k排序
* 二分

####
