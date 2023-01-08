# mihoyo

\##go 基础（伪代码）

* defer return 先后顺序
* 100个任务 每次执行在线不超过30 伪代码([https://geektutu.com/post/hpg-concurrency-control.html](https://geektutu.com/post/hpg-concurrency-control.html))
* 安全性map(defer) 伪代码
* slice 截取 数组之后，变不变
* context的应用，写一个超时伪代码
* pool高性能编程（[https://geektutu.com/post/hpg-sync-pool.html](https://geektutu.com/post/hpg-sync-pool.html)）

\##mysql

* 四种隔离级别读到的数据
* 评论表的设计[https://blog.csdn.net/u013107634/article/details/89556973](https://blog.csdn.net/u013107634/article/details/89556973)
* varchar char区别
* int(1) int(10)
* 索引失效两个例子([https://blog.csdn.net/JMW1407/article/details/109507453](https://blog.csdn.net/JMW1407/article/details/109507453))

\##redis

* 雪崩（redis过期时间随机、二级缓存过期时间不一样）
* 穿透（布隆过滤器，不存在直接返回[https://www.51cto.com/article/704389.html](https://www.51cto.com/article/704389.html)）
* 分布式锁（原子、超时、重防锁）
* 榜单key的设置（zadd、zrevrange、zrevrank、zincrby，zrem，同分问题：分数+'.'+（MAx-时间戳）），分数越大越好，时间戳越小越好-[https://juejin.cn/post/6844903795131056135](https://juejin.cn/post/6844903795131056135)
* 无序集合

\##kafka

* 增加消费者速度（[https://www.51cto.com/article/713177.html](https://www.51cto.com/article/713177.html)）
* 保证消息的有序性（从消费者角度）（[https://cloud.tencent.com/developer/article/2079904](https://cloud.tencent.com/developer/article/2079904)）

\##算法

后序层次遍历带(#)（[https://leetcode.cn/problems/binary-tree-postorder-traversal/solution/er-cha-shu-de-hou-xu-bian-li-by-leetcode-solution/](https://leetcode.cn/problems/binary-tree-postorder-traversal/solution/er-cha-shu-de-hou-xu-bian-li-by-leetcode-solution/)）

\##场景

* 流量激增长，访问过载如何解决：限流，熔断、服务降级、队列延迟处理、访问计数、漏桶、令牌桶、时间窗口（[https://z.itpub.net/article/detail/F86A54C3BDB42080F9AD1DDC012FD35F](https://z.itpub.net/article/detail/F86A54C3BDB42080F9AD1DDC012FD35F)）

