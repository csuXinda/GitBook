---
description: Mysql
---

# Mysql

#### 锁

* 读写锁（共享锁、排他锁）

&#x20;          select ... lock in share mode

&#x20;          select ...for update

* 行表锁

&#x20;          innodb myislam

* 乐观锁、悲观锁

乐观锁的思路一般是表中增加版本字段，更新时where语句中增加版本的判断，算是一种CAS（Compare And Swep）操作，商品库存场景中number起到了版本控制（相当于version）的作用（ AND number=#{number}）。悲观锁之所以是悲观，在于他认为本次操作会发生并发冲突，所以一开始就对商品加上锁（SELECT ... FOR UPDATE），然后就可以安心的做判断和更新，因为这时候不会有别人更新这条商品库存。#那么它加的是行锁还是表锁，这就要看是不是用了索引/主键。没用索引/主键的话就是表锁，否则就是是行锁#

* 间隙锁

可重复读隔离级别下解决幻读问题，防止新数据插入

#### 分布式数据库

* 分片 （[https://juejin.cn/post/6974939567053307918](https://juejin.cn/post/6974939567053307918)）

&#x20;      mycat，newsql，TiDB

#### binlog工具

canal vs maxcell [https://cloud.tencent.com/developer/article/1630490](https://cloud.tencent.com/developer/article/1630490)

