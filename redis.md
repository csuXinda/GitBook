# Redis

#### 缓存 数据一致性，延时双删方案[https://www.51cto.com/article/705167.html](https://www.51cto.com/article/705167.html)

#### cluster slot [https://zhuanlan.zhihu.com/p/129105249](https://zhuanlan.zhihu.com/p/129105249)

#### 集群模式 分布式锁

[https://tonybai.com/2021/02/13/operate-with-shared-resources-in-a-mutually-exclusive-way-through-distributed-lock-implemented-by-redis-cluster/](https://tonybai.com/2021/02/13/operate-with-shared-resources-in-a-mutually-exclusive-way-through-distributed-lock-implemented-by-redis-cluster/)

#### 缓存击穿

缓存的数据在db存在，在缓存中不存在失效

* 热点数据不过期，或者加基础过期时间+随机时间
* 分布式锁，缓存过期后，先用分布式锁从数据库加载完后加载到内存

#### 缓存穿透

访问不存在的数据

* 缓存不存在的id
* 布隆过滤器

#### 缓存雪崩

缓存雪崩指的是大量的请求无法在 Redis 缓存系统中处理，请求全部打到数据库，导致数据库压力激增，甚至宕机

* 过期时间加随机值
* 限流，缓存失效后从数据库加载到缓存

### 数据持久化存储-RDB-AOF

数据恢复。

redis 服务异常，aof 比 rdb 更有利于数据恢复。aof 默认每秒将数据增量追加到文件末存盘一次，rdb 是一个时间点的数据快照，时间跨度比较大。

数据备份。

rdb 是 redis 内存数据快照，速度快，体积小。更适合于数据备份存储。

redis 服务启动速度。

redis 启动加载 rdb 文件 比 aof 快。 因为 aof 文件有冗余命令，rdb 是数据集合。

持久化速度。

aof 默认每秒存盘和 rdb 持久化都是异步存储，基本不影响主线程主逻辑功能。如果 aof 采用写命令实时存盘，将会严重影响 redis 服务性能。

集群节点间全量同步。

集群节点间数据全量同步，需要拷贝服务进程的内存数据，根据 rdb 持久化特点：速度快，体积小，显然 rdb 更适合于集群间数据传输。

