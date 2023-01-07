# shenxinfu

### binlog 同步&#x20;

* cancal 主从同步 主->线程->binlog->从->relaylog->重放（完全同步、半同步（多slave，其中一个确认），异步）（[https://help.aliyun.com/document\_detail/273086.html](https://help.aliyun.com/document\_detail/273086.html)）
*   redo log是磁盘顺序写，数据刷盘是磁盘随机写，磁盘的顺序写比随机写高效的多啊。

    这种先预写日志后面再将数据刷盘的机制，有一个高大上的专业名词——WAL（Write-ahead logging），翻译成中文就是预写式日志。
* statement、行级、mixed

### workflow 配置文件同步依赖、argo flow 对比（k8s云原生、每个流都在自己pod里面运行，利用率不高）

### k8s怎么路由到pod(iptables)

### 俩协程交替打印奇偶1-100

### 容器底层（namespace，cgroup，unionFS）（[https://www.51cto.com/article/709751.html](https://www.51cto.com/article/709751.html)）

### 没有golang的pprof trace 如何定位进程内存、CPU

* golang自带go tool，pprof或者trace采集，定位CPU、内存代码段，弊端：程序中断
* 通用解决方案
* （1）CPU：top -> gdb(dlv) attach定位CPU占用高的协程（例子：死循环，select default空操作，频繁GC，死锁（取决于锁的实现，while尝试，自选锁，而不是sleep睡眠状态））([https://blog.csdn.net/liuhui251435428/article/details/106177611](https://blog.csdn.net/liuhui251435428/article/details/106177611))([https://blog.51cto.com/u\_15127539/4388975](https://blog.51cto.com/u\_15127539/4388975))
* （2）mem：[https://panzhongxian.cn/cn/2020/12/memory-leak-problem-1/](https://panzhongxian.cn/cn/2020/12/memory-leak-problem-1/)（例子：[https://www.modb.pro/db/415926](https://www.modb.pro/db/415926)）
*   （3）mysql IO负载高：磁盘子系统设备性能差，或采用ext2/ext3之类文件系统，或采用cfq之类的io scheduler，所以IOPS提上不去；

    SQL效率不高，比如没有索引，或者一次性读取大量数据，所以需要更多的I/O；

    可用内存太小，内存中能缓存/缓冲的数据不多，所以需要更多的I/O。调整buffer\_pool,innodb\_io\_capacity
* （4）mysql CPU 高：
  * 慢查询：建议使用 DBbrain 来排查和优化，详情请参见 [慢查询](https://cloud.tencent.com/document/product/236/35416#mcx)。
  * 计算量大：因处理数据量大，导致 CPU 利用率过高，处理措施详情请参见 [计算量大](https://cloud.tencent.com/document/product/236/35416#jsld)。
  * 高 QPS：因访问量过大，导致 CPU 利用率过高，处理措施详情参见 [高 QPS](https://cloud.tencent.com/document/product/236/35416#gqps)。

### golang maxprocs 容器里面如何设置cpu核数（[https://jishuin.proginn.com/p/763bfbd5b76c](https://jishuin.proginn.com/p/763bfbd5b76c)）

### GMP chan缓冲、无缓冲 底层架构

[https://juejin.cn/post/7129085275266875422](https://juejin.cn/post/7129085275266875422)



###

###

