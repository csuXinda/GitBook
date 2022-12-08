# 算法

#### 红黑树 vs AVL（[https://www.cnblogs.com/sxkgeek/p/9349931.html](https://www.cnblogs.com/sxkgeek/p/9349931.html)）

红黑树是通过复杂的节点插入、节点颜色变换后实现的：这些功能经典的AVL树也能实现，为什么要提出红黑树？

首先红黑树是不符合AVL树的平衡条件的，即每个节点的左子树和右子树的高度最多差1的二叉查找树。但是提出了为节点增加颜色，红黑是用非严格的平衡来换取增删节点时候旋转次数的降低，任何不平衡都会在三次旋转之内解决，而AVL是严格平衡树，因此在增加或者删除节点的时候，根据不同情况，旋转的次数比红黑树要多。所以红黑树的插入效率更高！！！

对于插入删除操作很少，又很频繁地查询的，可以用红黑树实现