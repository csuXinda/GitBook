# 场景题

#### 高并发设计经验（[https://mp.weixin.qq.com/s/PPQzMOZ\_1t19hFdTO60xKA](https://mp.weixin.qq.com/s/PPQzMOZ\_1t19hFdTO60xKA)）

#### 秒杀系统（[https://www.cnblogs.com/chanshuyi/p/how-to-design-a-second-killing-system.html](https://www.cnblogs.com/chanshuyi/p/how-to-design-a-second-killing-system.html)）

* 前端（**页面静态化 + CDN」、请求频率限制进行优化**）
* 后端（**一般有「增加缓存层 + 预热数据」、「MQ 异步处理」、「限流、熔断、降级」、业务侧优化这 4 种优化方式。**）

#### 设计RPC

#### 短链接（[https://xie.infoq.cn/article/483fcfbe3f942cb1fa9d9ce20](https://xie.infoq.cn/article/483fcfbe3f942cb1fa9d9ce20)）

* \->短链请求，生成方式：hash（URL 附加上特殊字符串，直到躲开哈希冲突）,统一发号器(snowflake,redis自增长，mysql自增长)
* \->302临时重定向，每次浏览器都会向服务器发起请求获取新的地址，虽然会给服务器增加压力（301直接去浏览器缓存获取，缺点不能实时更新点赞等数据）
* \->布隆过滤器（防止缓存击穿，造成服务器压力过大）
* \->缓存数据
* \->数据库

#### 排行榜

* 榜单key的设置（zadd、zrevrange、zrevrank、zincrby，zrem，同分问题：分数+'.'+（MAx-时间戳）），分数越大越好，时间戳越小越好-[https://juejin.cn/post/6844903795131056135](https://juejin.cn/post/6844903795131056135)

#### 微信抢红包（[https://www.infoq.cn/article/2017hongbao-weixin](https://www.infoq.cn/article/2017hongbao-weixin)）

* 对比分析：方案一：内存代替db操作，可以提高并发能力，但是可能出现数据丢失情况，不适用于资金交易系统；方案二：db乐观锁代替悲观锁，事物回滚和并发大小会影响用户体验
* SET 化、请求排队串行化、memcached cas控制并发，维度分库

#### 设计点赞功能

#### 微博feed流、朋友圈



#### [分布式定时任务](https://yeqown.xyz/2022/01/27/%E8%AE%BE%E8%AE%A1%E4%B8%80%E4%B8%AA%E5%88%86%E5%B8%83%E5%BC%8F%E5%AE%9A%E6%97%B6%E4%BB%BB%E5%8A%A1%E7%B3%BB%E7%BB%9F/)

* raft选主
* rabbitmq
* 一致性哈希分配

分布式id、锁、事务（[https://www.cnblogs.com/chengxy-nds/p/12315917.html](https://www.cnblogs.com/chengxy-nds/p/12315917.html)）（）

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
