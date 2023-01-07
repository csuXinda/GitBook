# k8s

* 面试总结（[https://juejin.cn/post/7070507980952698911](https://juejin.cn/post/7070507980952698911)）
* linux底层

Docker 在 Linux 的底层技术有：Namespaces（资源隔离）、CGroups （资源限制）、UnionFS （联合文件系统）（便于镜像的分层继承）

* cgroup [https://www.cnblogs.com/sammyliu/p/5886833.html](https://www.cnblogs.com/sammyliu/p/5886833.html)，在cgroup文件下面限制CPU、MEM
* namespaces([https://cizixs.com/2017/08/29/linux-namespace/](https://cizixs.com/2017/08/29/linux-namespace/))

| 名称                 | 宏定义              | 隔离的内容                                                                                                                                                                            |
| ------------------ | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IPC(进程通信隔离)        | CLONE\_NEWIPC    | System V IPC, POSIX message queues (since Linux 2.6.19)                                                                                                                          |
| Network（网络隔离）      | CLONE\_NEWNET    | network device interfaces, IPv4 and IPv6 protocol stacks, IP routing tables, firewall rules, the /proc/net and /sys/class/net directory trees, sockets, etc (since Linux 2.6.24) |
| Mount（文件挂载隔离）      | CLONE\_NEWNS     | Mount points (since Linux 2.4.19)                                                                                                                                                |
| PID（进程号隔离）         | CLONE\_NEWPID    | Process IDs (since Linux 2.6.24)                                                                                                                                                 |
| User（用户隔离）         | CLONE\_NEWUSER   | User and group IDs (started in Linux 2.6.23 and completed in Linux 3.8)                                                                                                          |
| UTS（node和domain隔离） | CLONE\_NEWUTS    | Hostname and NIS domain name (since Linux 2.6.19)                                                                                                                                |
| Cgroup             | CLONE\_NEWCGROUP | Cgroup root directory (since Linux 4.6)                                                                                                                                          |

* docker layer（[https://developer.aliyun.com/article/981453](https://developer.aliyun.com/article/981453)）
* Docker 容器中的每一层只读的 image，以及最上层可读写的文件系统，均被称为 layer。如此一来，layer 的范畴比 image 多了一层，即多包含了最上层的 read-write filesystem

docker 持久化存储的两种方式 [https://www.yisu.com/zixun/23274.html](https://www.yisu.com/zixun/23274.html)

**1）bind mount（用户管理）：**将宿主机上的某个目录或文件（不可以是没有格式化的磁盘文件），挂载到容器中，默认在容器内对此目录是有读写权限的，如果只需要向容器内添加文件，不希望覆盖目录，需要注意源文件必须存在，否则会被当做一个目录bind mount给容器。\
**2）docker manager volume（docker自动管理）：**不需要指定源文件，只需要指定mount point（挂载点）。把容器里面的目录映射到了本地。

* docker 网络 host bridge none，通过iptables通信[https://www.cnblogs.com/hahaha111122222/p/13370773.html](https://www.cnblogs.com/hahaha111122222/p/13370773.html)

（1）host 使用主机的network，不会产生network 隔离和网卡

（2）bridge产生network namespace和docker0网卡通信

（3）k8s(寻址) **`kube-proxy的pod通过监听集群中service和endpoints资源的变化，刷新节点上的iptables`**[https://juejin.cn/post/7134143215380201479](https://juejin.cn/post/7134143215380201479)

### 权限管理 [https://huweicai.com/kubernetes-permissions-overview/](https://huweicai.com/kubernetes-permissions-overview/)

### 云原生资料库 [https://lib.jimmysong.io/](https://lib.jimmysong.io/)

### lstio envoy sidecar [https://www.modb.pro/db/236348](https://www.modb.pro/db/236348)

### [https://www.cnblogs.com/ZhuChangwu/p/16464316.html](https://www.cnblogs.com/ZhuChangwu/p/16464316.html)
