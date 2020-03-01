# 如何使用本篇文档？





**规范**





[TOC]





# 简介

## 历史

## 配置

**安装**

一键式安装

**命令行工具**

```bash
编译文件：到go代码目录下，执行go build hello.go
```

## 开发环境





# 基本语法

**标识符**

标识符可以是字母，数字，下划线组成。但开头不能是数字

**关键字**



**注释**

go语言使用C风格注释

```go
/*这是块级注释*/
//这是行注释
```



# 数据类型

**声明**

```go
//变量的声明必须用空格隔开
var age int;

//短变量声明，声明时不需要指定类型。自动初始化成合适的类型
i, j := 0, 10  // python中叫海象运算符
```

## 布尔类型

## 数字类型

## 字符串类型

## 派生类型

## 类型转换

# 运算符

```go
//算术运算符
+
-
*
/
%
++
--

//关系运算符
==
!=
>
<
>=
<=

//逻辑运算符
&&
||
!

//位运算符
&
|
^

//赋值运算符
=
:=
+=
-=
*=
/=
%=
<<=
>>=
&=
^=
!=

//指针运算符
&  //返回变量存储地址
*  //指针变量

//优先级
5  * / % << >> & &^
4  + - | ^
3  == != < <= > >=
2  &&
1  ||






```



# 语句

**行分隔符**

Go语言中，一行代表一个语句结束，编译器在结尾处自动添加分号。如果打算将多个语句写在一行，则必须使用分号

## 条件语句

```go
if a < 20 {
  //true code
} else {
  //false code
}
```

## 循环语句

```go

```





# 函数



```go
func main()
{//错误，这里的左括号不能单独放在一行
  //代码风格统一
}

func add(a int, b int) int {
  var sum int
  sum = a + b
  return sum
}
```

如果代码里有未使用的变量，则无法编译，这种设计是为了减轻代码维护量

```go
func calc(a int, b int)(int,int){
  sum := a + b
  avg := (a+b)/2
  return sum, avg //一个函数可以有多个返回值
}
```





# 作用域

# 指针

# 复合数据类型

数组，结构体，Map





# 包

程序中绝大多数的函数都是别人写的，作者只需要思考其中一部分。然后可以通过包来复用

模块化允许包在不同的项目中共享，复用，在组织中发布，或者在全世界范围内使用

**包的导入**


```go
import "fmt"  //导入单个包
import (//导入多个包
  "fmt"
  "math/rand"//导入路径
  "encoding/json"
  "golang.org/x/net/html"//域名
  "github.com/go-sql-driver/mysql"
)

import (
  "fmt"
  "html/template"
  "os"
//插入空行进行分组
  "golang.org/x/net/html"
  "golang.org/x/net/ipv4"
)

import (
  "crypto/rand"
  mrand "math/rand"//重命名导入
//替代名字仅影响当前文件
//如果导入的包名非常冗长，也可以使用替代名字
//使用替代名字避免包名和文件中的变量名冲突
)
```

**包的声明**

```go
package main  //包名通常是路径的最后一段，如果路径不同，包名可以相同
```

**包内的变量**

包内的变量大写，其他包也可以使用

包内的变量如果是小写，其他包不可以使用

**实例**

```go
如何导入自定义包
// go/main.go
package main
import "./test"

// go/test/g.go
package test

//自定义的包必须写对路径名，和文件名
//main包必须要有
```







# 并发

基于CSP (Communicating Sequential Process 通信顺序进程)模型实现



go语句



channel

管道，类似于unix/linux中的pipe

多个goroute之间通过channel进行通信

```go
func main(){
  pipe := make(chan int, 3)//new一个管道，容量是3
  pipe <- 1  //把1放进管道里
  pipe <- 2
}//管道的内部结构是队列，先进先出
```





# 其他

```go
import "fmt"
fmt.Println("Hello")
```









# 链接

社区网站

[Go语言官网](https://golang.google.cn)

[Go语言中文社区](https://studygolang.com)

[Golang中国](https://www.golangtc.com)

优质文章

[Go语言是面向对象语言吗？](https://blog.csdn.net/li_101357/article/details/80205005)

# 参考书目

《Go程序设计语言》[美]艾伦A.A.多诺万,布莱恩W.柯尼汉 机械工业出版社 ISBN 978-7111558422

*The Go Programming Language* Alan A. A. Donovan · Brian W. Kernighan ISBN: 978-0134190440

同本异名书籍-Go语言圣经

[随书源码](http://www.gopl.io)

[中文版 网上译版](https://github.com/gopl-zh/gopl-zh.github.com)



《》..