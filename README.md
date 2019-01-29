# go_learning_way

推荐 https://github.com/yangwenmai/learning-golang
go  学习笔记

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
              func 作为代码片段
              函数作为小片段，被当做函数使用，应该 不用 压栈入栈那些，所以代价小
            2、闭包  ”内联“ 的语句 or 表达式。会在 使用的地方、方法内形成内存，即局部性，（优越性：可以直接使用函数内变量，不用声明）
            http://www.shouce.ren/api/view/a/5605 即调用第一次，会生成一个局部内存块。
            有点类似 对象，new 之后，object的变量属于这个object,这个变量在这个object 内一直生效;你再次new 之后，新的变量属于新的object.
             
            3、方法  一个包含了 ”接受者“ 的函数
            func (variable_name variable_data_type) function_name() [return_type]{
                      /* 函数体*/
              }
              
              就是把  函数参数 变成 一个对象、struct 。感觉比函数代价大，对象、struct 自身很大（不过写代码会方便很多）。
              
12、作用域： 变量 的作用范围

作用域为已声明标识符所表示的常量、类型、变量、函数或包在源代码中的作用范围。

函数内定义的变量称为局部变量
函数外定义的变量称为全局变量
函数定义中的变量称为形式参数

局部变量
边界之内可见，边界之外不可见

全局变量
全都可见

不同类型的局部和全局变量默认值为：
int	0
float32	0
pointer	nil

13、数组
声明：
var  balance [10] float32

初始化


var balance = [5]float32{100.0,2.0,3.4,7.0,50.0}

 var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}

float salary = balance[4]

多维数组    &&   向函数传递数组

var threedim [5][10][4]int
a = [3][4]int{  
 {0, 1, 2, 3} ,   /*  第一行索引为 0 */
 {4, 5, 6, 7} ,   /*  第二行索引为 1 */
 {8, 9, 10, 11}   /*  第三行索引为 2 */
}

int val = a[2][3]

void myFunction(param [10]int)
{
.
.
.
}

void myFunction(param []int)
{
.
.
.
}

14、指针
   var a int = 10   
   fmt.Printf("变量的地址: %x\n", &a  )
结果：
变量的地址: 20818a220

什么是指针：
一个地址，内存上存储数据的地址

如何使用指针
1、定义指针变量。==》2、为指针变量赋值。===》3、访问指针变量中指向地址的值。

   var a int= 20   /* 声明实际变量 */

   var ip *int        /* 1、声明指针变量 */
   ip = &a  /* 2、指针变量的存储地址 */

   /* 3、使用指针访问值 */
   fmt.Printf("*ip 变量的值: %d\n", *ip )

结果：

*ip 变量的值: 20

nil 指针也称为空指针。

nil在概念上和其它语言的null、None、nil、NULL一样，都指代零值或空值。

Go 指针数组    指向指针的指针    像函数传递指针参数

如果一个指针变量存放的又是另一个指针变量的地址，则称这个指针变量为指向指针的指针变量。

变量 a = 3000
指针变量 *ptr = 3000
指向指针的指针变量 **pptr = 3000


15、结构体  struct 
type struct_variable_type struct {
   member definition;
   member definition;
   ...
   member definition;
}

声明变量
   var Book1 Books        /* 声明 Book1 为 Books 类型 */
   Book1.title = "Go 语言"

variable_name := structure_variable_type {value1, value2...valuen}

访问成员
variable_name.member1  variable_name.member2

结构体指针
var struct_pointer *Books
struct_pointer = &Book1;
struct_pointer.title;

16、切片 Slice
定义
1、var identifier []type
2、var slice1 []type = make([]type, len)  ==> slice1 := make([]type,len)

也可以指定容量，其中capacity为可选参数。
make([]T, length, capacity)

初始化：  
s :=[] int {1,2,3 } 
s := arr[:] 
s := arr[startIndex:endIndex] 
s := arr[startIndex:] 
s :=make([]int,len,cap) 
 len() 方法获取长度。
 append() 和 copy() 函数
 
 
 17、range
     sum := 0
    for _, num := range nums {
        sum += num
    }

18、Map
一种无序的键值对的集合  key==》value

   var countryCapitalMap map[string]string
   countryCapitalMap = make(map[string]string)
   countryCapitalMap["France"] = "Paris"
   countryCapitalMap["Italy"] = "Rome"
   countryCapitalMap["Japan"] = "Tokyo"
   countryCapitalMap["India"] = "New Delhi"
   
      /* 使用 key 输出 map 值 */
   for country := range countryCapitalMap {
      fmt.Println("Capital of",country,"is",countryCapitalMap[country])
   }
   
   是否存在 
      captial, ok := countryCapitalMap["United States"]
   /* 如果 ok 是 true, 则存在，否则不存在 */
   if(ok){
      fmt.Println("Capital of United States is", captial)  
   }else {
      fmt.Println("Capital of United States is not present") 
   }
   
   删除
      delete(countryCapitalMap,"France");

19、函数递归
func recursion() {
   recursion() /* 函数调用自身 */
}

递归函数对于解决数学上的问题是非常有用的，就像计算阶乘，生成斐波那契数列等。

20、类型转换
type_name(expression)

var sum int = 127
var count int = 5

var avg float = float(sum) / float32(count)


21、接口

type  interface_name interface{
   method_name1 [return_type]
   method_name2 [return_type]
   method_name3 [return_type]
   ...
   method_namen [return_type]
}

/* 定义结构体 */
type struct_name struct {
   /* variables */
}

/* 实现接口方法 */
func (struct_name_variable struct_name) method_name1() [return_type] {
   /* 方法实现 */
}
...
func (struct_name_variable struct_name) method_namen() [return_type] {
   /* 方法实现*/
}

22、错误处理

type error interface {
    Error() string
}

func Sqrt(f float64) (float64, error) {
    if f < 0 {
        return 0, errors.New("math: square root of negative number")
    }
    // 实现
}


22、开发IDE
LiteIDE



23、go  mysql 操作   （参考 https://blog.csdn.net/kenkao/article/details/47857795）

import (
"database/sql"
	_ "github.com/go-sql-driver/mysql"
)

main()
// 初始化
	db , err := sql.Open("mysql", "root:root@tcp(127.0.0.1:3306)/baskball2019?charset=utf8")

插入
	sqlstr := "INSERT baskball_user (name,nick,sex,weixinid) values (?,?,?,?)"
	stmt, err := db.Prepare(sqlstr)
	checkErr(err)
	res, err := stmt.Exec("tony","xiaxia",1,"ghjkvgbhjnkmvgbhjnk")
	checkErr(err)

	id, err := res.LastInsertId()
	checkErr(err)
	fmt.Println(id)

// 查询

	rows, err := db.Query("SELECT * FROM baskball_user")
	checkErr(err)
	
	columns, _ := rows.Columns()
	scanArgs := make([]interface{}, len(columns))
	values := make([]interface{}, len(columns))
	for i := range values {
		scanArgs[i] = &values[i]
	}


	for rows.Next() {
		err = rows.Scan(scanArgs...)
		record := make(map[string]string)
		for i, col := range values {
			if col != nil {
				record[columns[i]] = string(col.([]byte))
			}
		}
    
    fmt.Println(record)
		fmt.Println(record["id"])
	}

// 修改
	sqlstr = "UPDATE baskball_user SET name=? WHERE id=?"
	stmt, err = db.Prepare(sqlstr)
	checkErr(err)
	res, err = stmt.Exec("nice", 1)
	checkErr(err)
	num, err := res.RowsAffected()
	checkErr(err)
	fmt.Println(num)
  
// 删除
	stmt, err = db.Prepare(`DELETE FROM baskball_user WHERE id=?`)
	checkErr(err)
	res, err = stmt.Exec(5)
	checkErr(err)
	num, err = res.RowsAffected()
	checkErr(err)
	fmt.Println(num)

go 语言中  =   :=  的异同
https://segmentfault.com/q/1010000007160096

=    必须先声明

:=   类型自动推断


确实是
============
1、
	var db *sql.DB
	var err error
	db , err = sql.Open("mysql", "root:root@tcp(127.0.0.1:3306)/baskball2019?charset=utf8")
  
2、	db , err := sql.Open("mysql", "root:root@tcp(127.0.0.1:3306)/baskball2019?charset=utf8")
============


24、go 文件读写操作



25、网络操作


26、redis 读写


27、日志的书写（应该也是写文件）


28、go  调试



29、go 框架
gin  beego























![知识树](https://github.com/KeKe-Li/For-learning-Go-Tutorial/blob/master/src/images/1.jpg)
