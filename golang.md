---
description: some
---

# Golang

## 语法

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
* g0 是什么？在 Go 中创建的所有 Goroutine 都会被一个内部的调度器所管理。Go 调度器尝试为所有的 Goroutine 分配运行时间，并且在当前的 Goroutine 阻塞或者终止的时候，Go 调度器会通过运行 Goroutine 的方式使所有 CPU 保持忙碌状态。这个调度器实际上是作为一个特殊的 Goroutine 运行的。Go 使用 `GOMAXPROCS` 变量限制同时运行的 OS 线程数量。
* interface（interface 是一种类型；interface 变量存储的是实现者的值）；可以通过断言判断变量的类型；`interface{}` 是一个空的 interface 类型，所有类型都实现了interface {}([https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/](https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/))
* 只有声明了但没赋值的interface才是nil interface([https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/](https://sanyuesha.com/2017/07/22/how-to-understand-go-interface/))



