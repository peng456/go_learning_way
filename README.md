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
程序一般由关键字、常量、变量、运算符、类型和函数组成。

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
          特殊 complex  copy imag nil panic recover  real uintptr
  
  常量 ： const num = 120
  变量： var age int
          
 运算符:  + - * /
 
 6、数据类型
 布尔类型： true or false  
          var b bool = true
 数字类型 ： int float   && 支持复数
           uint8、uint16、uint32、uint64、int8、int16、int32、int64
           
           float32、float64、complex64、complex128
           
           byte、rune、uint、int、uintptr
 
 字符串类型: string  (UTF-8编码标识Unicode文本)
 
 派生类型：
      Pointer 、数组、struct、union、函数（func）、切片（slic）、接口（interface）、Map、Channel
 
 7、变量
 var identifier type
8、值类型、引用

9、常量
const identifier [type] = value
const b = "abc"

iota 特殊常量（认为是一个可以被编译器修改的常量，可以自增）
        
10、运算符：
算数运算符： + - * / % ++ --
关系运算符： ==  !=  >  <  >=  <=  
逻辑运算符:  && ||  !  (判断真值)
位运算符:   &   |  ^   <<    >> (这是计算出结果)
赋值运算符:  =   +=   -=   *=   /=   %=   <<=   >>=   &=  ^=   |=
其他运算符:  & 返回变量存储地址   *  指针变量
运算符优先级: ........


11、条件语句
if 
if else

if 嵌套语句

switch 语句

select 语句   类似于用于通信的switch语句 ==>每个case必须是一个通信操作(发送 or 接收)

终止 && 跳转

break:经常用于中断当前 for 循环或跳出 switch 语句
continue:跳过当前循环的剩余语句，然后继续进行下一轮循环。
goto: 转移 ---》标记处，继续执行(可以无条件地转移到过程中指定的行)

for 循环
    for init; condition; post { }

11、函数

main()  入口函数

init() 包内 初始化函数，在加载的过程就会被执行

基础的
func function_name( [parameter list] ) [return_types]
{
   函数体
}

例子：
func max(num1, num2 int) int
{
   /* 声明局部变量 */
   result int
 
   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result 
}
函数返回多个值
func swap(x, y string) (string, string) {
   return y, x
}

func main() {
   a, b := swap("Mahesh", "Kumar")
   fmt.Println(a, b)
}

函数参数类型： 值传递   引用传递

默认情况下，Go 语言使用的是值传递，即在调用过程中不会影响到实际参数。

函数用法  :  1、函数作为值   函数本身是一个可以被用来给其他变量赋值的整体
            2、闭包  ”内联“ 的语句 or 表达式。会在 使用的地方、方法内形成内存，即局部性，（优越性：可以直接使用函数内变量，不用声明）
            http://www.shouce.ren/api/view/a/5605 即调用第一次，会生成一个局部内存块。
            3、方法
            func (variable_name variable_data_type) function_name() [return_type]{
                      /* 函数体*/
              }
























![知识树](https://github.com/KeKe-Li/For-learning-Go-Tutorial/blob/master/src/images/1.jpg)
