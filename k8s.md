# k8s

* 面试总结（[https://juejin.cn/post/7070507980952698911](https://juejin.cn/post/7070507980952698911)）
* linux底层

Docker 在 Linux 的底层技术有：Namespaces（资源隔离）、CGroups （资源限制）、UnionFS （联合文件系统）（便于镜像的分层继承）

* docker layer（[https://developer.aliyun.com/article/981453](https://developer.aliyun.com/article/981453)）
* Docker 容器中的每一层只读的 image，以及最上层可读写的文件系统，均被称为 layer。如此一来，layer 的范畴比 image 多了一层，即多包含了最上层的 read-write filesystem

docker 持久化存储的两种方式 [https://www.yisu.com/zixun/23274.html](https://www.yisu.com/zixun/23274.html)

**1）bind mount（用户管理）：**将宿主机上的某个目录或文件（不可以是没有格式化的磁盘文件），挂载到容器中，默认在容器内对此目录是有读写权限的，如果只需要向容器内添加文件，不希望覆盖目录，需要注意源文件必须存在，否则会被当做一个目录bind mount给容器。\
**2）docker manager volume（docker自动管理）：**不需要指定源文件，只需要指定mount point（挂载点）。把容器里面的目录映射到了本地。

### 权限管理 [https://huweicai.com/kubernetes-permissions-overview/](https://huweicai.com/kubernetes-permissions-overview/)

### 云原生资料库 [https://lib.jimmysong.io/](https://lib.jimmysong.io/)

### lstio envoy sidecar [https://www.modb.pro/db/236348](https://www.modb.pro/db/236348)

### [https://www.cnblogs.com/ZhuChangwu/p/16464316.html](https://www.cnblogs.com/ZhuChangwu/p/16464316.html)
