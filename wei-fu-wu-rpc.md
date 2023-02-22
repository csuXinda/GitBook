---
description: RPC
---

# 微服务 RPC

### RPC [https://juejin.cn/post/6982414578944573477](https://juejin.cn/post/6982414578944573477)

* GRPC尚未提供连接池，需要自行实现
* 尚未提供“服务发现”、“负载均衡”机制
* 因为基于HTTP2，绝大部多数`HTTP Server、Nginx`都尚不支持，即Nginx不能将GRPC请求作为HTTP请求来负载均衡，而是作为普通的TCP请求。（nginx1.9版本已支持）

\


### 微服务 [https://www.wangan.com/p/7fy78y5e5f98b339](https://www.wangan.com/p/7fy78y5e5f98b339)

### goMicro [https://www.topgoer.com/%E5%BE%AE%E6%9C%8D%E5%8A%A1/GoMicro%E5%85%A5%E9%97%A8.html](https://www.topgoer.com/%E5%BE%AE%E6%9C%8D%E5%8A%A1/GoMicro%E5%85%A5%E9%97%A8.html)
