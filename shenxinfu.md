# shenxinfu

### binlog 同步

### workflow 配置文件同步依赖、argo flow 对比（k8s云原生、每个流都在自己pod里面运行，利用率不高）

### k8s怎么路由到pod(iptables)

### 俩协程交替打印奇偶1-100

### 容器底层（namespace，cgroup，unionFS）（[https://www.51cto.com/article/709751.html](https://www.51cto.com/article/709751.html)）

### 没有golang的pprof trace 如何定位进程内存、CPU

* golang自带go tool，pprof或者trace采集，定位CPU、内存代码段，弊端：程序中断
* 通用解决方案
* （1）CPU：top -> gdb(dlv) attach定位CPU占用高的协程（例子：死循环，select default空操作，频繁GC）
* （2）mem：[https://panzhongxian.cn/cn/2020/12/memory-leak-problem-1/](https://panzhongxian.cn/cn/2020/12/memory-leak-problem-1/)（例子：[https://www.modb.pro/db/415926](https://www.modb.pro/db/415926)）

### golang maxprocs 容器里面如何设置cpu核数（[https://jishuin.proginn.com/p/763bfbd5b76c](https://jishuin.proginn.com/p/763bfbd5b76c)）

### GMP chan缓冲、无缓冲 底层架构



###

###

