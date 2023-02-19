---
description: some
---

# Golang

## 锁实现（[https://juejin.cn/post/7128348244983152654](https://juejin.cn/post/7128348244983152654)）

## 语法

#### make new区别

* make只适用分配类型为slice、map、chan，返回类型本身，new可以分配任意类型并且返回的指针
* new把分配的内存置为零

#### slice 和数组区别

* 数组是定长、值传递、申明指定大小
* slice动态，底层是指向数组，还有一个长度、容量，是引用传递

#### for range 地址变化

* 在for a,b := range c 遍历中， a 和b 在内存中只会存在一份，即之后每次循环时遍历到的数据都是以值覆盖的方式赋给a 和b，a，b 的内存地址始终不变。 由于有这个特性，「for 循环里面如果开协程，不要直接把a 或者b 的地址传给协程」

#### defer的坑[https://www.topgoer.com/%E5%87%BD%E6%95%B0/%E5%BB%B6%E8%BF%9F%E8%B0%83%E7%94%A8defer.html](https://www.topgoer.com/%E5%87%BD%E6%95%B0/%E5%BB%B6%E8%BF%9F%E8%B0%83%E7%94%A8defer.html)

* db循环退出
* 匿名函数打印
* 正常打印

#### go defer，多个 defer 的顺序，defer 在什么时机会修改返回值？（for defer）

「设置返回值—>执行defer—>ret」。defer可以修改函数最终返回值，修改时机：有名返回值或者函数返回指针

#### defer recover 的问题？(主要是能不能捕获)

* error 类型错误，不需要 recover 拯救
* 协程内的panic可以恢复，外的不行
* fatal 系统级错误不行

#### uint 类型溢出

* uint255+1 =0

#### 介绍 rune 类型

* byte 相当于int8，相当于一个ascill码
* rune相当于int32，对应一个unicode编码，可以占用4个字节
* 在中文的时候可以用rune来处理，中文utf-8 需要使用3个 byte

#### Golang 都是值传

在Go语言中只存在值传递，要么是值的副本，要么是指针的副本。无论是值类型的变量还是引用类型的变量亦或是指针类型的变量作为参数传递都会发生值拷贝，开辟新的内存空间。另外值传递、引用传递和值类型、引用类型是两个不同的概念，不要混淆了。引用类型作为变量传递可以影响到函数外部是因为发生值拷贝后新旧变量指向了相同的内存地址。

#### Golang 内存泄漏场景

* [https://www.cnblogs.com/CherryTab/p/12848811.html](https://www.cnblogs.com/CherryTab/p/12848811.html)
* 匿名函数
* 子字符串造成的内存泄露 （复制、string.Builder,string.Repeat）
* 子切片造成的内存泄露 （append）
* 延迟调用函数导致的临时性内存泄露 for里使用defer(sync.pool)

#### 内存泄漏如何检测 [https://mdnice.com/writing/17048155289049038a9aa88644ffc464](https://mdnice.com/writing/17048155289049038a9aa88644ffc464)

* &#x20;pprof&#x20;
* 单元测试 （uber-go/goleak）

#### Golang 内存逃逸

* 匿名函数
* 栈溢出
* 指针传递
*   逃逸分析基本原则 编译器会根据变量是否被外部引用来决定是否逃逸：

    如果函数外部没有引用，则优先放到栈中； 如果函数外部存在引用，则必定放到堆中; 如果栈上放不开，则必定放到堆上;
* go build 时，配合使用参数 -gcflags

#### 传值 VS 传指针&#x20;

「函数传递指针真的比传值效率高吗？如果拷贝的数据量小，由于指针传递会产生逃逸，可能会使用堆，增加垃圾回收(GC)的负担，所以传递指针不一定 是高效的。」

#### Golang struct 能不能比较 [https://juejin.cn/post/6881912621616857102](https://juejin.cn/post/6881912621616857102)

*   #### reflect.DeepEqual



#### 闭包（[http://c.biancheng.net/view/59.html](http://c.biancheng.net/view/59.html)）

* 函数 + 引用环境 = 闭包

#### context

* 用于控制goroutine的整个生命周期，进行上下文的管理
* 结构：[https://draveness.me/golang/docs/part3-runtime/ch06-concurrency/golang-context/](https://draveness.me/golang/docs/part3-runtime/ch06-concurrency/golang-context/)

#### context 应用场景

* rpc调用
* http value传值
* 超时控制
* pipeline控制



####

















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







