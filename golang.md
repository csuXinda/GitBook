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



