# go_learning_way


go 

1、起源  谷歌开发的。。。。。（企业背书好）

2、安装
我的是mbp ,直接 brew install go 

3、Hello World! 
test.go
package main

import "fmt"

func main( {
  fmt.Println("Hello world ！！！") 
}

命令行执行

go run test.go

运行结果：
Hello, World!

3、语言结构
语言基础： 
  包声明、
  引入包、
  函数、
  变量、
  语句&表达式 
  注释

4、go 编译执行过程（比如如何引入包，如何初始化，init 函数执行的顺序等）（先略，以后补充）

5、基础语法
  分隔符： 一行代表一句
  注释： 不会被编译
        单行注释：  //
        多行注释：  /*
                    Author by shouce.ren菜鸟教程
                    我是多行注释
                   */
  标识符： 名字规则差不多   
  关键字:  25 个（今天 就用了type,与 关键字冲突）
          特殊的 func、defer、go、chan、fallthrough、range、select、type ==> 这些go 独有的  
          **** 还有 36 个预定义标识符。。。。。。这就后好多
          特殊
        







![知识树](https://github.com/KeKe-Li/For-learning-Go-Tutorial/blob/master/src/images/1.jpg)
