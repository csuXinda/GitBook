---
description: some
---

# Golang

## 锁实现（[https://juejin.cn/post/7128348244983152654](https://juejin.cn/post/7128348244983152654)）

## 语法

* golang 参数传递方式都是值传递，指针会发生copy（[https://www.flysnow.org/2018/02/24/golang-function-parameters-passed-by-value](https://www.flysnow.org/2018/02/24/golang-function-parameters-passed-by-value)）
* slice append会生成一个新的数组(超出长度的话)
* for...range 里面临时变量被复用，&只取最后的赋值，fix：值传递
* `接口实现，Student` 和 `*Student` 是两种类型
*   iota是golang语言的常量计数器,只能在常量的表达式中使用。

    iota在const关键字出现时将被重置为0(const内部的第一行之前)，const中每新增一行常量声明将使iota计数一次(iota可理解为const语句块中的行索引)。
* more [https://github.com/lifei6671/interview-go/blob/master/question/q008.md](https://github.com/lifei6671/interview-go/blob/master/question/q008.md)
* defer 延迟调用时，需要保存函数指针和参数，因此链式调用的情况下，除了最后一个函数/方法外的函数/方法都会在调用时直接执行。也就是说 `t.f(1)` 直接执行，然后执行 `fmt.Print(3)`，最后函数返回时再执行 `.f(2)`，因此输出是 132。（[https://geektutu.com/post/qa-golang-c1.html](https://geektutu.com/post/qa-golang-c1.html)）
* go net epoll([https://learnku.com/articles/59847)](https://learnku.com/articles/59847)
* 场景题（[https://blog.51cto.com/u\_8887390/3308860](https://blog.51cto.com/u\_8887390/3308860)）
* 布隆过滤器（[https://juejin.cn/post/6844903982209449991](https://juejin.cn/post/6844903982209449991)）
* g0 是什么？在 Go 中创建的所有 Goroutine 都会被一个内部的调度器所管理。Go 调度器尝试为所有的 Goroutine 分配运行时间，并且在当前的 Goroutine 阻塞或者终止的时候，Go 调度器会通过运行 Goroutine 的方式使所有 CPU 保持忙碌状态。这个调度器实际上是作为一个特殊的 Goroutine 运行的。Go 使用 `GOMAXPROCS` 变量限制同时运行的 OS 线程数量。（[https://studygolang.com/articles/28443](https://studygolang.com/articles/28443)）
* interface（interface 是一种类型；interface 变量存储的是实现者的值）；可以通过断言判断变量的类型；`interface{}` 是一个空的 interface 类型，所有类型都实现了interface {}([https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/](https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/))
* 只有声明了但没赋值的interface才是nil interface([https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/](https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/))
* 内存逃逸 [https://juejin.cn/post/7140864963974791175](https://juejin.cn/post/7140864963974791175)
* 内存泄漏 [https://www.modb.pro/db/415926](https://www.modb.pro/db/415926)
* gc 堆还是栈 [https://blog.csdn.net/csdniter/article/details/103617531](https://blog.csdn.net/csdniter/article/details/103617531)
* mutex实现：自选锁+FIFO队列，会产生饿汉模式([https://github.com/flycash/interview-baguwen/blob/main/golang/mutex.md](https://github.com/flycash/interview-baguwen/blob/main/golang/mutex.md))
* 抢占式调度（[https://www.wenwoha.com/7/course\_article?act\_id=59\&is\_comment=Yes](https://www.wenwoha.com/7/course\_article?act\_id=59\&is\_comment=Yes)）

新版本：运行时间过长强行释放CPU，基于信号，旧版本：，垃圾回收

* gc 触发场景

（1）手动触发（2）堆空间达到阀值，上一次gc超时

**三色标记法：**

对象有黑白灰三色

1. stop the world
2. 将根对象全部标记为灰色
3. start the world
4. 在goroutine中进行对灰色对象进行遍历， 将灰色对象引用的每个对象标记为灰色，然后将该灰色对象标记为黑色。
5. 重复执行4， 直接将所有灰色对象都变成黑色对象。
6. stop the world，清除所有白色对象

这里4，5是与用户程序是并发执行的，所以stw的时间被大大缩短了。 不过这样做可能会导致新创建的对象被误清除，因此使用了写屏障技术来解决该问题，大体逻辑是当创建新对象时将新对象置为灰色。

* golang channel nil close 区别（[https://zhuanlan.zhihu.com/p/564848742](https://zhuanlan.zhihu.com/p/564848742)）+ select case channel(nil)的话这条分支读写永久阻塞，相当于失效
* timer ticker 用法（[https://zhuanlan.zhihu.com/p/564848742](https://zhuanlan.zhihu.com/p/564848742)）







