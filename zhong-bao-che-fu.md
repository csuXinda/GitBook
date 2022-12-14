# 中保车服

* 来源ip
* body 安全
* 请求次数限制（redis expire incr [https://blog.51cto.com/u\_15127579/2722263](https://blog.51cto.com/u\_15127579/2722263)）
* 签名
* https
* 要点
* [https://cloud.tencent.com/developer/article/1777870](https://cloud.tencent.com/developer/article/1777870)
  * 请求是否合法：是否是我的信任方
  * 请求是否被篡改：是否被第三方劫持并篡改参数
  * 防止重复请求（防重放）：是否重复请求

加密过程：[https://developer.engage-all.com/backend/open-api.html#hmac-%E8%AF%B7%E6%B1%82%E7%AD%BE%E5%90%8D%E3%80%81%E5%93%8D%E5%BA%94%E6%B5%81%E7%A8%8B](https://developer.engage-all.com/backend/open-api.html#hmac-%E8%AF%B7%E6%B1%82%E7%AD%BE%E5%90%8D%E3%80%81%E5%93%8D%E5%BA%94%E6%B5%81%E7%A8%8B)





#### Redis的内存淘汰策略（[https://juejin.cn/post/6844903927037558792](https://juejin.cn/post/6844903927037558792)）

*   **noeviction(默认策略)**：对于写请求不再提供服务，直接返回错误（DEL请求和部分特殊请求除外）

    **allkeys-lru**：从所有key中使用LRU算法进行淘汰

    **volatile-lru**：从设置了过期时间的key中使用LRU算法进行淘汰

    **allkeys-random**：从所有key中随机淘汰数据

    **volatile-random**：从设置了过期时间的key中随机淘汰

    **volatile-ttl**：在设置了过期时间的key中，根据key的过期时间进行淘汰，越早过期的越优先被淘汰
* LRU LFU

#### openapi（百度，dto->mdo body的一个加密）

#### k8s -(pvc，文件共享，联合文件系统，kubelab，namespace、cgroup）

#### https加密过程 http 三次握手，大量timewait（[http://www.yunweipai.com/40430.html](http://www.yunweipai.com/40430.html)）

#### DNS寻址过程([https://juejin.cn/post/6866457093256249351#heading-2](https://juejin.cn/post/6866457093256249351#heading-2))

缓存->本地host->域名服务器（递归）

#### 反转链表

#### 构建加速 - 共享存储

#### mysql 容灾

* 读写分离 [gorm DBResolver](https://gorm.io/zh\_CN/docs/dbresolver.html)
* 主备可以双向同步
* 半同步复制 keepalive自动切换，双主模式会引起主键冲突，单主从+keepalive+探测脚本+vip（[https://bbs.huaweicloud.com/blogs/114439](https://bbs.huaweicloud.com/blogs/114439)）

#### prometheus采集，自定义metric [https://www.cnblogs.com/ifnk/p/15917374.html](https://www.cnblogs.com/ifnk/p/15917374.html)

* PromQL [https://juejin.cn/post/6994980341366652935](https://juejin.cn/post/6994980341366652935)

### golang 协程

**协程的特点：**

1. 有独立的栈空间
2. 共享程序堆空间
3. 调度由用户控制
4. 协程是轻量级的线程

**协程的优点：**

1. 代码编辑简单。可以将异步处理逻辑代码用同步的方式编写，将多个异步操作集中到一个函数中完成。
2. 单线程模式，没有线程安全的问题，不需要加锁操作。
3. 性能好。协程是用户态线程，切换更加高效。

#### CSP

* Golang 就是借用CSP模型的一些概念为之实现并发进行理论支持，其实从实际上出发，go语言并没有，完全实现了CSP模型的所有理论，仅仅是借用了 process和channel这两个概念。process是在go语言上的表现就是 goroutine 是实际并发执行的实体，每个实体之间是通过channel通讯来实现数据共享。https://www.jianshu.com/p/36e246c6153d&#x20;

#### 调度器生命周期 [https://learnku.com/articles/41728](https://learnku.com/articles/41728)
