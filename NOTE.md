# note

## 技巧

* STAR 法则，Situation,Target,Action,Result

## ElasticSearch

* \[别名]\([https://www.cnblogs.com/chenhuabin/p/13800715.html)](https://www.cnblogs.com/chenhuabin/p/13800715.html)
* \[架构]\([https://github.com/YVictor13/ElasticSearch-study/blob/master/src/Elasticsearch%20%E6%9E%B6%E6%9E%84%E8%AE%BE%E8%AE%A1%E5%8F%8A%E8%AF%B4%E6%98%8E.md)](https://github.com/YVictor13/ElasticSearch-study/blob/master/src/Elasticsearch%20%E6%9E%B6%E6%9E%84%E8%AE%BE%E8%AE%A1%E5%8F%8A%E8%AF%B4%E6%98%8E.md)
* 倒排（全文索引）
* cardinality高基数（[https://cloud.tencent.com/developer/article/1769165）](https://cloud.tencent.com/developer/article/1769165)

## Linux

### 操作系统

* I/O多路复用中select/poll/epoll的区别

三大调度算法-CPU、内存、磁盘[https://cloud.tencent.com/developer/article/1695055](https://cloud.tencent.com/developer/article/1695055)

### 多路复用、水平触发、边缘触发

{% embed url="https://juejin.cn/post/7009997944782848007" %}

[https://www.modb.pro/db/18965](https://www.modb.pro/db/189656)

### [https://juejin.cn/post/7091951675384004621](https://juejin.cn/post/7091951675384004621)

### 进程

进程是系统实际运行的程序，是资源分配的最小单。进程之前通信可以通过管道、信号量、共享内存、队列或者socket。一个进程可以有多个线程，同一个进程内线程共享进程资源。线程运行在CPU上，实现进程内的并发，切换比较快，开销较少。

* fork linux创建进程的函数，分配资源空间
*   如果父进程先退出，子进程还没退出那么子进程的父进程将变为init进程（托孤给了init进程）。（注：任何一个进程都必须有父进程）

    如果子进程先退出，父进程还没退出，那么子进程必须等到父进程捕获到了子进程的退出状态才真正结束，否则这个时候子进程就成为僵进程（僵尸进程：只保留一些退出信息供父进程查询）
* 进程调度[https://juejin.cn/post/7088325691988508702](https://juejin.cn/post/7088325691988508702)
* shell

```shell
# 进程树
pstree -p  |grep -C 10 1608
# 进程
ps -aux |grep PID
# 线程
ps -T -p 16089   
top -H -p 16089
```

* PCB\
  进程作为运行中的程序，需要一个结构体记录执行信息，每个进程都只在CPU中运行很短时间，CPU拿到内存指针就知道进程相关信息 struct结构体包括标识符pid、状态status、上下文、优先级、CPU内存等相关信息 ![img\_4.png](<img/img\_4 (1).png>)
* 进程调度
* 堆栈\
  ![img\_1.png](<img/img\_1 (1).png>)\
  （1）静态（全局）存储区——static：内存在程序编译的时候就已经分配好，这块内存在程序的整个运行期间都存在。它主要存放静态数据、全局数据和常量。也是程序结束后，由操作系统释放。\
  （2）栈区——stack：后进先出，在执行函数时，函数参数，局部变量（包括const局部变量），函数调用后返回的地址都在栈上创建，函数执行结束时这些存储单元自动被释放。栈内存分配运算内置于处理器的指令集中，效率很高，但是分配的内存容量有限。\
  （3）堆区——heap：亦称动态内存分配。堆排序利于优先级，程序在运行的时候用malloc或new申请任意大小的内存，程序员自己负责在适当的时候用free或 delete释放内存。动态内存的生存期可以由我们决定，如果我们不释放内存，程序将在最后才释放掉动态内存。如果某动态内存不再使用，需要将其释放掉，否则，内存泄漏。

### tcp

* 协议基础

{% embed url="https://juejin.cn/post/6844903582550982669" %}

[https://juejin.cn/post/6844903582550982669](https://juejin.cn/post/6844903582550982669)

* socket编程

[https://blog.csdn.net/mccand1234/article/details/91346202](https://blog.csdn.net/mccand1234/article/details/91346202)

```shell
# fd(一切皆文件）  
 ll /proc/PID/fd
```

![img\_2.png](<img/img\_2 (1).png>)

* tcpdump

```shell
 tcpdump -i eth1  -nn -s0 -vv  port 80 -w new_test.pacp
```

* pcap
* 线程生命周期 ![img.png](img.png)
* [内存虚拟地址物理地址映射](https://blog.51cto.com/u\_15169172/4711723)

## http

* nginx [https://juejin.cn/post/7070028214659186702](https://juejin.cn/post/7070028214659186702)
* http https [https://juejin.cn/post/6844903471565504526](https://juejin.cn/post/6844903471565504526)
* 输入Url过程，DOMAIN->DNS->IP->TCP CONNECT->RESPONSE->CLIENT EXTRACT

### header

* [jwt认证](https://learnku.com/go/t/52399)
* base认证

### payload

### burp

## Golang

### \[GC]\( [https://just ejin.cn/post/7111515970669117447)](https://juejin.cn/post/7111515970669117447)

（[https://juejin.cn/post/7040737998014513183](https://juejin.cn/post/7040737998014513183)）

### [GMP模型](https://www.kancloud.cn/aceld/golang/1958305#2GolangGMP\_2)

* [https://juejin.cn/post/6956605745022369805#heading-14](https://juejin.cn/post/6956605745022369805#heading-14)
* 线程(thread)内核线程，协程(goroutine)用户线程。一个“用户态线程”必须要绑定一个“内核态线程”，但是CPU并不知道有“用户态线程”的存在，它只知道它运行的是一个“内核态线程”(Linux的PCB进程控制块)。 频繁进程/线程切换/多线程/多进程，造成CPU、内存消耗。M:N提高CPU利用率。GM引入P(Processor)调度器，把可运行的goroutine分配到工作线程上(M)，利用队列缓存和P之间的G调度减少M锁，提高利用率。\
  ![img.png](<img/img (1).png>)
* CSP并发模型

### [调试优化](https://cloud.tencent.com/developer/article/1469185)

* pprof
* go test
* go bench

```shell
go test -bench . -run none -benchmem -cpuprofile cpuprofile.out -memprofile memprofile.out
```

### map

## Python

\###[爬虫](https://cuiqingcai.com/archives/)

### 迭代器&&生成器

## Docker

## Kubernetes

* [架构](https://juejin.cn/post/7007362174843060255)
* sidecar&#x20;
* service mesh 服务网格通过`SideCar`之后，服务节点只做业务逻辑自身的功能，服务之间的调用只需交给`SideCar`，由`SideCar`完成注册服务、服务发现、请求路由、熔断限流、日志统计等业务无关功能。
* lsito(一种service mesh框架)
* 面试题目 [https://www.51cto.com/article/706611.html](https://www.51cto.com/article/706611.html)

## Security

## BigData

### Flink

* Maxwell mysql to kafka [https://www.jianshu.com/p/12b9bcb983cb](https://www.jianshu.com/p/12b9bcb983cb)

### ClickHouse

### Hadoop

### MongoDB

### Mysql

## ETC ZOOKEEPER CAP 乐观锁、悲观锁

乐观锁：不加锁，更新时需要判断冲突，悲观锁:读写加锁\
悲观锁比较适合强一致性的场景，但效率比较低，特别是读的并发低。乐观锁则适用于读多写少，并发冲突少的场景。

### CAP

* CA without P：如果不要求P（不允许分区），则C（强一致性）和A（可用性）是可以保证的。但放弃P的同时也就意味着放弃了系统的扩展性，也就是分布式节点受限，没办法部署子节点，这是违背分布式系统设计的初衷的。传统的关系型数据库RDBMS：Oracle、MySQL就是CA。
* CP without A：如果不要求A（可用），相当于每个请求都需要在服务器之间保持强一致，而P（分区）会导致同步时间无限延长(也就是等待数据同步完才能正常访问服务)，一旦发生网络故障或者消息丢失等情况，就要牺牲用户的体验，等待所有数据全部一致了之后再让用户访问系统。设计成CP的系统其实不少，最典型的就是分布式数据库，如Redis、HBase等。对于这些分布式数据库来说，数据的一致性是最基本的要求，因为如果连这个标准都达不到，那么直接采用关系型数据库就好，没必要再浪费资源来部署分布式数据库。
* AP wihtout C：要高可用并允许分区，则需放弃一致性。一旦分区发生，节点之间可能会失去联系，为了高可用，每个节点只能用本地数据提供服务，而这样会导致全局数据的不一致性。典型的应用就如某米的抢购手机场景，可能前几秒你浏览商品的时候页面提示是有库存的，当你选择完商品准备下单的时候，系统提示你下单失败，商品已售完。这其实就是先在 A（可用性）方面保证系统可以正常的服务，然后在数据的一致性方面做了些牺牲，虽然多少会影响一些用户体验，但也不至于造成用户购物流程的严重阻塞。

### Redis

* 列表最大长度2^32-1，40亿
* [https://zhuanlan.zhihu.com/p/91539644](https://zhuanlan.zhihu.com/p/91539644)
* redis分布式锁
* 原子操作
* lua
* [https://juejin.cn/post/6936956908007850014](https://juejin.cn/post/6936956908007850014)
* \[跳表]\([https://www.jianshu.com/p/9d8296562806](https://www.jianshu.com/p/9d8296562806))
* 集群模式 [https://www.jianshu.com/p/fe7b7800473e](https://www.jianshu.com/p/fe7b7800473e)
* raft和gossip（[https://cloud.tencent.com/developer/article/1357901](https://cloud.tencent.com/developer/article/1357901)）[https://cloud.tencent.com/developer/article/1826426](https://cloud.tencent.com/developer/article/1826426)
* 事务和pipeline（[http://redisguide.com/pipeline-and-transaction.html](http://redisguide.com/pipeline-and-transaction.html)）

### [分布式锁](https://juejin.cn/post/6844903830442737671)

### 不重复有序集合

不同的是每个元素都会关联一个double类型的分数。redis正是通过分数来为集合中的成员进行从小到大的排序。

### Git

### Kafka

\[架构]（[https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E5%88%86%E5%B8%83%E5%BC%8F%E4%B8%AD%E9%97%B4%E4%BB%B6%E5%AE%9E%E8%B7%B5%E4%B9%8B%E8%B7%AF%EF%BC%88%E5%AE%8C%EF%BC%89/13%20%E6%B7%B1%E5%85%A5%E8%A7%A3%E8%AF%BB%E5%9F%BA%E4%BA%8E%20Kafka%20%E5%92%8C%20ZooKeeper%20%E7%9A%84%E5%88%86%E5%B8%83%E5%BC%8F%E6%B6%88%E6%81%AF%E9%98%9F%E5%88%97%E5%8E%9F%E7%90%86.md](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E5%88%86%E5%B8%83%E5%BC%8F%E4%B8%AD%E9%97%B4%E4%BB%B6%E5%AE%9E%E8%B7%B5%E4%B9%8B%E8%B7%AF%EF%BC%88%E5%AE%8C%EF%BC%89/13%20%E6%B7%B1%E5%85%A5%E8%A7%A3%E8%AF%BB%E5%9F%BA%E4%BA%8E%20Kafka%20%E5%92%8C%20ZooKeeper%20%E7%9A%84%E5%88%86%E5%B8%83%E5%BC%8F%E6%B6%88%E6%81%AF%E9%98%9F%E5%88%97%E5%8E%9F%E7%90%86.md)）

\[消息可靠性]（[https://www.jianshu.com/p/da61d521d088](https://www.jianshu.com/p/da61d521d088)）





### Mysql&#x20;

[来源](https://juejin.cn/post/7136352977614274574)

[https://cloud.tencent.com/developer/article/1543335](https://cloud.tencent.com/developer/article/1543335)

* b树和b+树
* innodb和MyISAM
* 聚集索引和非聚集索引[https://cloud.tencent.com/developer/article/1541265](https://cloud.tencent.com/developer/article/1541265)
* [分表](https://zq99299.github.io/note-book/back-end-storage/03/01.html#%E5%B0%8F%E7%BB%93)
* 事务 [https://juejin.cn/post/6844903665367547918](https://juejin.cn/post/6844903665367547918)
* 优化 expain 覆盖索引 最左匹配原则 [https://juejin.cn/post/6945838953605890055](https://juejin.cn/post/6945838953605890055)

### 数据结构

* b树、b+树、avl树，红黑树
* 二叉树，左子树大于右子树，先序、中序、后序、层次遍历[https://blog.csdn.net/Lyon\_Nee/article/details/119171977](https://blog.csdn.net/Lyon\_Nee/article/details/119171977)

### 算法

* 递归
* 动态规划
* 排序
* [https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0070.%E7%88%AC%E6%A5%BC%E6%A2%AF%E5%AE%8C%E5%85%A8%E8%83%8C%E5%8C%85%E7%89%88%E6%9C%AC.md](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0070.%E7%88%AC%E6%A5%BC%E6%A2%AF%E5%AE%8C%E5%85%A8%E8%83%8C%E5%8C%85%E7%89%88%E6%9C%AC.md)

### [reset rebase revert](https://blog.nowcoder.net/n/a9cb57d9343b43b8a645ca8ba3dd46cd)
