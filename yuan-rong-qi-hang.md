# 元戎启行

### 红黑树 vs hash表

* hash表 O(1),内存大，空间换时间，当更多的数插入时，哈希表冲突的可能性就更大O(n)，resize哈希表的过程将会是一个非常消耗时间的过程。例如，如果现在你的哈希表的长度是100，但是现在有第101个数要插入。这时，不仅哈希表的长度可能要扩展到150，且扩展之后所有的数都需要重新rehash。
* 哈希表中的元素是没有被排序的
* 红黑树，若搜索的次数远远大于插入和删除，那么选择AVL，如果搜索，插入删除次数几乎差不多，应该选择RB。

#### top K ip(数据倾斜问题)（[https://leetcode.cn/problems/interleaving-string/solution/jiao-cuo-zi-fu-chuan-by-leetcode-solution/](https://leetcode.cn/problems/interleaving-string/solution/jiao-cuo-zi-fu-chuan-by-leetcode-solution/)）

#### 线程安全 CAS 原子性操作、automicAdd

{% embed url="https://www.cnblogs.com/ricklz/p/13648859.html" %}

* &#x20;automic.add automic.load automic.store&#x20;
* CompareAndSwap swap

####

####

