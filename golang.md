---
description: some
---

# Golang

## 语法

* slice append会生成一个新的数组
* for...range 里面临时变量被复用，&只取最后的赋值，fix：值传递
* `接口实现，Student` 和 `*Student` 是两种类型
*   ota是golang语言的常量计数器,只能在常量的表达式中使用。

    iota在const关键字出现时将被重置为0(const内部的第一行之前)，const中每新增一行常量声明将使iota计数一次(iota可理解为const语句块中的行索引)。
* more [https://github.com/lifei6671/interview-go/blob/master/question/q008.md](https://github.com/lifei6671/interview-go/blob/master/question/q008.md)