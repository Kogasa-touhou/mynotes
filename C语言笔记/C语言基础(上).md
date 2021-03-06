<!-- vscode-markdown-toc -->
* 1. [主要结构](#)
	* 1.1. [编译&运行C程序](#C)
* 2. [基础语法](#-1)
	* 2.1. [C的令牌（Token）](#CToken)
	* 2.2. [分号 ;](#-1)
	* 2.3. [注释](#-1)
	* 2.4. [标识符](#-1)
	* 2.5. [关键字](#-1)
	* 2.6. [C中的空格](#C-1)
* 3. [C数据类型](#C-1)
	* 3.1. [整数类型](#-1)
	* 3.2. [浮点类型](#-1)
	* 3.3. [void类型](#void)
	* 3.4. [数值类型转换](#-1)
* 4. [变量](#-1)
	* 4.1. [变量的定义](#-1)
	* 4.2. [变量的声明](#-1)
	* 4.3. [C 中的左值（Lvalues）和右值（Rvalues）](#CLvaluesRvalues)
* 5. [C常量](#C-1)
	* 5.1. [整数常量](#-1)
	* 5.2. [浮点常量](#-1)
	* 5.3. [字符常量](#-1)
	* 5.4. [字符串常量](#-1)
	* 5.5. [定义常量](#-1)
* 6. [C 运算符](#C-1)
	* 6.1. [算数运算符](#-1)
	* 6.2. [关系运算符](#-1)
	* 6.3. [逻辑运算符](#-1)
	* 6.4. [位运算符](#-1)
	* 6.5. [赋值运算符](#-1)
	* 6.6. [杂项运算符  sizeof & 三元](#sizeof)
	* 6.7. [C 中的运算符优先级](#C-1)
* 7. [C 判断](#C-1)
	* 7.1. [if 语句](#if)
	* 7.2. [switch 语句](#switch)
* 8. [C 循环](#C-1)
	* 8.1. [循环类型](#-1)
	* 8.2. [循环控制语句](#-1)
* 9. [C 函数](#C-1)
	* 9.1. [函数声明](#-1)
	* 9.2. [调用函数](#-1)
	* 9.3. [函数参数](#-1)
	* 9.4. [占位符](#-1)
* 10. [作用域规则](#-1)
	* 10.1. [局部变量](#-1)
	* 10.2. [全局变量](#-1)
	* 10.3. [形式参数](#-1)
	* 10.4. [初始化局部变量和全局变量](#-1)
* 11. [数组](#-1)
	* 11.1. [声明数组](#-1)
	* 11.2. [初始化数组](#-1)
	* 11.3. [访问数组元素](#-1)
* 12. [enum(枚举)](#enum)
	* 12.1. [枚举变量的定义](#-1)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->
# C语言基础(上)

##  1. <a name=''></a>主要结构  

C语言主要包括以下结构:  
+ 预处理器指令  
+ 函数  
+ 变量 
+ 语句&表达式  
+ 注释  

> "Hello World"实例  
```c
#include <stdio.h>
/*
预处理器指令↑
主函数↓
*/
int main() {
    /*我的第一个C语言程序*/
    printf("Hello World! \n");
    system("pause"); //暂停函数，请按任意键继续...
    return 0;
    /*终止main()函数，并返回值0*/
}
```
###  1.1. <a name='C'></a>编译&运行C程序  
+ 使用编辑器键入代码
+ 保存为 xxx.c
+ 打开终端，cd到指定的目录  
+ 键入 gcc xxx.c 回车。编译代码  
+ 如果没有报错，将生成可执行文件（xxx.out/xxx.exe）  
+ 键入可执行文件运行程序

如果是多个c代码的源码文件，编译方法如下:  
```shell 
$ gcc test1.c test2.c -o main.out
$ ./main.out
可用 gcc [源文件名] -o [目标文件名] 来指定目标文件路径及文件名
```

##  2. <a name='-1'></a>基础语法  

###  2.1. <a name='CToken'></a>C的令牌（Token）

C语言由各种令牌组，可以是关键字、标识符、常量、字符串、符号等。
例如:  
```c
printf("Hello World!"\n);
```

令牌分别是: printf  (   "Hello World!"\n    )    ;      五个


###  2.2. <a name='-1'></a>分号 ;

分号代表着语句的结束，表明一个逻辑实体的结束
请不要写成中文的分号  

###  2.3. <a name='-1'></a>注释  

注释有两种方式:  
```c
//单行注释

/* 单行注释 */

/*
    多行注释
    多行注释
    多行注释
*/
```
注释不可以相互嵌套  

###  2.4. <a name='-1'></a>标识符  

C语言的标识符用来标识变量、函数，或者任何其他用户自定义项目的名称。
以A-Z，a-z，下划线_开始，后接0个或者多个字母、下划线和数字(0-9)  
区分大小写  
标识符内不允许出现标点字符(@ $ %等)

###  2.5. <a name='-1'></a>关键字  

<table>
    <tr>
        <td>关键字</td>
        <td>说明</td>
    </tr>
    <tr>
        <td>auto</td>
        <td>声明自动变量 </td>
    </tr>
    <tr>
        <td>break</td>
        <td>跳出当前循环 </td>
    </tr>
    <tr>
        <td>case</td>
        <td>开关语句分支</td>
    </tr>
    <tr>
        <td>char</td>
        <td>声明字符型变量或函数返回值类型</td>
    </tr>
    <tr>
        <td>const</td>
        <td>定义常量，如果一个变量被 const 修饰，那么它的值就不能再被改变</td>
    </tr>
    <tr>
        <td>continue</td>
        <td>结束当前循环，开始下一轮循环 </td>
    </tr>
    <tr>
        <td>default</td>
        <td>开关语句中的"其它"分支</td>
    </tr>
    <tr>
        <td>do</td>
        <td>循环语句的循环体</td>
    </tr>
    <tr>
        <td>double</td>
        <td>声明双精度浮点型变量或函数返回值类型</td>
    </tr>
    <tr>
        <td>else</td>
        <td>条件语句否定分支（与 if 连用）</td>
    </tr>
    <tr>
        <td>enum</td>
        <td>声明枚举类型</td>
    </tr>
    <tr>
        <td>extern</td>
        <td>声明变量或函数是在其它文件或本文件的其他位置定义</td>
    </tr>
    <tr>
        <td>float</td>
        <td>声明浮点型变量或函数返回值类型</td>
    </tr>
    <tr>
        <td>for</td>
        <td>一种循环语句</td>
    </tr>
    <tr>
        <td>goto</td>
        <td>无条件跳转语句</td>
    </tr>
    <tr>
        <td>if</td>
        <td>条件语句</td>
    </tr>
    <tr>
        <td>int</td>
        <td>声明整型变量或函数</td>
    </tr>
    <tr>
        <td>long</td>
        <td>声明长整型变量或函数返回值类型</td>
    </tr>
    <tr>
        <td>register</td>
        <td>声明寄存器变量</td>
    </tr>
    <tr>
        <td>return</td>
        <td>子程序返回语句(可以带参数，也可不带参数)</td>
    </tr>
    <tr>
        <td>short</td>
        <td>声明短整型变量或函数</td>
    </tr>
    <tr>
        <td>signed</td>
        <td>声明有符号类型变量或函数</td>
    </tr>
    <tr>
        <td>sizeof</td>
        <td>计算数据类型或变量长度（即所占字节数）</td>
    </tr>
    <tr>
        <td>static</td>
        <td>声明静态变量 </td>
    </tr>
    <tr>
        <td>struct</td>
        <td>声明结构体类型 </td>
    </tr>
    <tr>
        <td>switch</td>
        <td>用于开关语句 </td>
    </tr>
    <tr>
        <td>typedef</td>
        <td>用以给数据类型取别名 </td>
    </tr>
    <tr>
        <td>unsigned</td>
        <td>声明无符号类型变量或函数 </td>
    </tr>
    <tr>
        <td>union</td>
        <td>声明共用体类型 </td>
    </tr>
    <tr>
        <td>void</td>
        <td>声明函数无返回值或无参数，声明无类型指针 </td>
    </tr>
    <tr>
        <td>volatile</td>
        <td>说明变量在程序执行中可被隐含地改变 </td>
    </tr>
    <tr>
        <td>while</td>
        <td>循环语句的循环条件 </td>
    </tr>
</table>

C99新增关键字  
<table>
    <td>_Bool</td>
    <td>_Complex</td>
    <td>_Imaginary</td>
    <td>inline</td>
    <td>restrict</td>
</table>

C11新增关键字  
<table>
    <td>_Alignas</td>
    <td>_Alignof</td>
    <td>_Atomic</td>
    <td>_Generic</td>
    <td>_Noreturn</td>
    <td>_Static_assert</td>
    <td>_Thread_local</td>
</table>  

###  2.6. <a name='C-1'></a>C中的空格 

空行会被编译器忽视  
空格用于描述空白符、制表符、换行符以及注释  
```c
people = man + woman
```
这几个之间的空格不是必要的但是为了增加可读性，可以适当添加  

##  3. <a name='C-1'></a>C数据类型  
数据类型指的是用于声明不同类型的变量或者函数的一个广泛的系统  
其类型决定了存储占用的空间，以及解释存储的位模式  

<table>
    <tr>
        <td>序号</td>
        <td>类型与描述</td>
    </tr>
    <tr>
        <td>1</td>
        <td>基本类型: 它们是算术类型，包括两种类型：整数类型和浮点类型</td>
    </tr>
    <tr>
        <td>2</td>
        <td>枚举类型：
它们也是算术类型，被用来定义在程序中只能赋予其一定的离散整数值的变量</td>
    </tr>
    <tr>
        <td>3</td>
        <td>void 类型：
类型说明符 void 表明没有可用的值</td>
    </tr>
    <tr>
        <td>4</td>
        <td>派生类型：
它们包括：指针类型、数组类型、结构类型、共用体类型和函数类型。
</td>
    </tr>
</table>

###  3.1. <a name='-1'></a>整数类型  

整数类型的存储大小和值范围的细节: 
<table>
    <tr>
        <td>类型</td>
        <td>存储大小</td>
        <td>值范围</td>
    </tr>
    <tr>
        <td>char</td>
        <td>1字节</td>
        <td>-128到127或者0到255</td>
    </tr>
    <tr>
        <td>unsigned char</td>
        <td>1字节</td>
        <td>0到255</td>
    </tr>
    <tr>
        <td>signed char</td>
        <td>1字节</td>
        <td>-128到127</td>
    </tr>
    <tr>
        <td>int</td>
        <td>2或4字节</td>
        <td>-32,768 到 32,767 或 -2,147,483,648 到 2,147,483,647</td>
    </tr>
    <tr>
        <td>unsigned int</td>
        <td>2或4字节</td>
        <td>0 到 65,535 或 0 到 4,294,967,295</td>
    </tr>
    <tr>
        <td>short</td>
        <td>2字节</td>
        <td>-32,768 到 32,767</td>
    </tr>
    <tr>
        <td>unsigned short</td>
        <td>2字节</td>
        <td>0 到 65,535</td>
    </tr>
    <tr>
        <td>long</td>
        <td>4字节</td>
        <td>-2,147,483,648 到 2,147,483,647</td>
    </tr>
    <tr>
        <td>unsigned long</td>
        <td>4字节</td>
        <td>0 到 4,294,967,295</td>
    </tr>
</table>

可以使用 __sizeof__ 运算符来得到对象或类型的存储字节大小。

+ sizeof(object); //sizeof(对象)
+ sizeof(type_name); //sizeof(类型)；
+ sizeof object; //sizeof 对象;

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    printf("int 存储大小 : %lu \n", sizeof(int));

    return 0;
}

```

###  3.2. <a name='-1'></a>浮点类型  

标准浮点类型的存储大小、值范围和精度的细节: 

<table>
    <tr>
        <td>类型</td>
        <td>存储大小</td>
        <td>值范围</td>
        <td>精度</td>
    </tr>
    <tr>
        <td>float</td>
        <td>4字节</td>
        <td>1.2E-38 到 3.4E+38</td>
        <td>6 位有效位</td>
    </tr>
    <tr>
        <td>double</td>
        <td>8 字节</td>
        <td>2.3E-308 到 1.7E+308</td>
        <td>15 位有效位</td>
    </tr>
    <tr>
        <td>long double</td>
        <td>16 字节</td>
        <td>3.4E-4932 到 1.1E+4932</td>
        <td>19 位有效位</td>
    </tr>
</table>

###  3.3. <a name='void'></a>void类型  

void 类型指定没有可用的值  

<table>
    <tr>
        <td>序号</td>
        <td>类型与描述</td>
    </tr>
    <tr>
        <td>1</td>
        <td>函数返回为空  
C 中有各种函数都不返回值，或者您可以说它们返回空。不返回值的函数的返回类型为空。例如 void exit (int status);</td>
    </tr>
    <tr>
        <td>2</td>
        <td>函数参数为空  
C 中有各种函数不接受任何参数。不带参数的函数可以接受一个 void。例如 int rand(void);</td>
    </tr>
    <tr>
        <td>3</td>
        <td>指针指向 void  
类型为 void * 的指针代表对象的地址，而不是类型。例如，内存分配函数 void *malloc( size_t size ); 返回指向 void 的指针，可以转换为任何数据类型。</td>
    </tr>
</table>

###  3.4. <a name='-1'></a>数值类型转换  
C语言中如果一个表达式中含有不同类型的常量和变量，在计算时，会自动将其转化为同一种类型。我们同样也可以对其进行强制的类型转换  

自动转换规则 ： 
+ 浮点数赋给整型，该浮点数小数被舍去；
+ 整数赋给浮点型，数值不变，但是被存储到相应的浮点型变量中； 

强制类型转换 ：
+ 强制类型转换形式: (类型说明符)(表达式)  

##  4. <a name='-1'></a>变量  
其本质就是程序可以操作的存储区的名称  
每个变量都有特定的类型:  

| 类型 | 描述 |
| :---:| :--: |
|char|通常是一个字节（八位）, 这是一个整数类型。| 
|int|整型，4 个字节，取值范围 -2147483648 到 2147483647。|
|float|单精度浮点值。单精度是这样的格式，1位符号，8位指数，23位小数。|
|double|双精度浮点值。双精度是1位符号，11位指数，52位小数。|
|void|表示类型的缺失。|  

###  4.1. <a name='-1'></a>变量的定义  
格式 : 
```c 
type variable_list;

int i,j,k;
char c,ch;
float f;
double d;

type variable_name = value;

extern int d = 3,f = 5;  //d和f的声明和初始化 

```

###  4.2. <a name='-1'></a>变量的声明  
为确保在编译的时候指定的类型和名称存在，所以在程序连接编译器的时候需要实际的变量声明   
有两种方式  
+ int a这种在声明的时候已经建立了存储空间  
+ 另外一种不需要建立存储空间的，使用extern关键字声明变量
+ 除非有extern关键字，否则就是变量的定义 

注意:  
+ 变量在使用前就要被定义或者声明  
+ 在一个程序中，变量只能定义一次，却可以声明多次  
+ 定义分配存储空间，而声明不会

```c
extern int i; //声明不是定义 
int i;      //声明，也是定义  

```

如果需要在一个源文件中引用另外一个源文件中定义的变量，我们只需在引用的文件中将变量加上 extern 关键字的声明即可。  
```c 
//声明外部变量
//addtwonum.c
#include <stdio.h>
extern int x ;
extern int y ;

int addtwonum() {
    return x + y ;
}
```

```c
//test.c
#include <stdio.h>
//定义全局变量  
int x = 1;
int y = 2;
int addtwonum() ;
int main(void) {
    int result ;
    result = addtwonum();
    printf("result为: %d\n",result) ;
    return 0 ;
}
```
```bash
$ gcc addtwonum.c test.c -o main
$ ./main
result 为: 3
```

###  4.3. <a name='CLvaluesRvalues'></a>C 中的左值（Lvalues）和右值（Rvalues）
C中有两种类型的表达式  
+ 左值 (lvalue) : 指向内存位置的表达式被称为左值（lvalue）表达式。左值可以出现在赋值号的左边或右边  
+ 右值 (rvalue) : 术语右值（rvalue）指的是存储在内存中某些地址的数值。右值是不能对其进行赋值的表达式，也就是说，右值可以出现在赋值号的右边，但不能出现在赋值号的左边  

变量是左值所以可以出现在赋值符号的左边，数值型的字面值是右值。因此不能被赋值 

总结: 
+  当需要保存数据的时候，需要lvalues
+  当需要读取数据的时候，需要rvalues  
lvalues 和 rvalues 角色的相互转换  
+ 根据表达式的上下文情况，lvalues 在需要 rvalues 的地方会自动转换为 rvalues 
```c 
int n;
int m;
m = n + 2; //表达式里的n就是rvalues

```

+ rvalues永远不能转换为lvalues


##  5. <a name='C-1'></a>C常量 

在程序执行期间不会改变的值称之为常量，又叫字面量  
常量可以是任意的数据类型  
和常规的变量类似只不过在定义之后不能被修改  


###  5.1. <a name='-1'></a>整数常量  

整数常量可以是十进制、八进制或者十六进制的常量  
关于前缀: 
+ 0x 或者 0X 表示十六进制
+ 0 表示八进制  
+ 不带前缀默认表示十进制  
关于后缀:  
+ 是U和L的组合 
+ U表示无符号整数(unsigned)
+ L表示长整数(long) 
+ 后缀可以是大写也可以是小写 ， U和L的顺序任意  

例子：
```c
212         /* 合法的 */
215u        /* 合法的 */
0xFeeL      /* 合法的 */
078         /* 非法的：8 不是八进制的数字 */
032UU       /* 非法的：不能重复后缀 */

85         /* 十进制 */
0213       /* 八进制 */
0x4b       /* 十六进制 */
30         /* 整数 */
30u        /* 无符号整数 */
30l        /* 长整数 */
30ul       /* 无符号长整数 */
```

###  5.2. <a name='-1'></a>浮点常量

浮点常量由整数部分、小数点、小数部分和指数部分组成  
可以使用小数形式或者指数形式来表示浮点常量  
使用小数形式:  
    必须包含整数部分、小数部分或者同时包含两种  
使用指数形式:  
    必须包含小数点、指数或者同时包含两者  
带符号的指数都是用e或者E 引入  


###  5.3. <a name='-1'></a>字符常量  

字符常量使用单引号表示  
字符常量可以是一个普通的字符、一个转义序列或者一个通用的字符  

转义字符表:

|转移序列|含义|
|:---:|:---:|
|\\| \ 字符 |
|\'| ' 字符 |
|\"| " 字符 |
|\0| 空字符 |
|\?| ? 字符 | 
|\a| 报警铃声|
|\b| 退格键 |
|\f| 换页符 |
|\n| 换行符 |
|\r| 回车 |
|\t| 水平制表符 |
|\v| 垂直制表符 |
|\ooo| 一到三位的八进制数 |
|\xhh...| 一个或多个数字的十六进制数 |

###  5.4. <a name='-1'></a>字符串常量  

字符串常量用双引号表示  
包含类似于字符常量的字符：普通的字符、转义序列和通用的字符  
可以使用空格做分隔符将很长的字符串进行分行  

###  5.5. <a name='-1'></a>定义常量  

有两种简单的定义常量的方式 
+ 使用 #define 预处理器  
+ 使用 const 关键字  

> #define 预处理器 

```c
#define identifier value
```

> const 关键字  

使用const前缀声明指定类型的常量  

```c
const type variable = value;
```
![](https://kogasaimgbed.oss-cn-beijing.aliyuncs.com/noteimgs/20220604123047.png)

注意：const声明常量需要在一个语句内完成 

常量一般使用纯大写字母这是一个好习惯  


##  6. <a name='C-1'></a>C 运算符 

C 语言有以下的运算符 :
+ 算数运算符 
+ 关系运算符  
+ 逻辑运算符  
+ 位运算符 
+ 赋值运算符 
+ 杂项运算符

###  6.1. <a name='-1'></a>算数运算符  

A 为 10 ，B 为 20 
|运算符|描述|实例|
|:-:|:-:|:-:|
|+|把两个操作数相加|A + B 为 30|
|-|从第一个操作数中减去第二个操作数|A - B 为 -10|
|*|把两个操作数相乘|A * B 为 200|
|/|分子除以分母| B / A 为 2 |
|%|取模运算符，整除后的余数| B % A 为 0|
|++|自增运算符，整数值+1| A++ 为 11 |
|--|自减运算符，整数值-1| A-- 为 9|

注意: a++是先赋值后运算，++a是先运算后赋值  

###  6.2. <a name='-1'></a>关系运算符  

|运算符|描述|
|:-:|:-:|
|==|检查两个操作数的值是否相等，如果相等则条件为真|
|!=|检查两个操作数的值是否相等，如果不相等则条件为真|
|>|检查左操作数的值是否大于右操作数的值，如果是则条件为真|
|<|检查左操作数的值是否小于右操作数的值，如果是则条件为真|
|>=|检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真|
|<=|检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真|

###  6.3. <a name='-1'></a>逻辑运算符  

|运算符|描述|
|:-:|:-:|
|&&|称为逻辑与运算符。如果两个操作数都非零，则条件为真|
|\|\||称为逻辑或运算符。如果两个操作数中有任意一个非零，则条件为真|
|!|称为逻辑非运算符。用来逆转操作数的逻辑状态。如果条件为真则逻辑非运算符将使其为假|

###  6.4. <a name='-1'></a>位运算符  

位运算符作用于位，并逐位执行操作  

真值表:  
|p|q|p & q|p \| q|p ^ q|
|:-:|:-:|:-:|:-:|:-:|
|0|0|0|0|0|
|0|1|0|1|1|
|1|1|1|1|0|
|1|0|0|1|1|

例:  
如果 A = 60， 且 B = 13  
以二进制形式表示  
A = 0011 1100  
B = 0000 1101  

A & B = 0000 1100 
A | B = 0011 1101
A ^ B = 0011 0001
~A = 1100 0011  

|运算符|描述|
|:-:|:-:|
|&|按与操作，按二进制位进行"与"运算|
|\||按位或运算符，按二进制位进行"或"运算|
|^|异或运算符，按二进制位进行"异或"运算|
|~|取反运算符，按二进制位进行"取反"运算|
|<<|二进制左移运算符。将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）|
|>>|二进制右移运算符。将一个数的各二进制位全部右移若干位，正数左补0，负数左补1，右边丢弃|


> 原码、反码和补码  
原码：一个整数，按照绝对值大小转换成的二进制数，称为原码  
反码：将二进制数按位取反，所得的新二进制数称为原二进制数的反码
    反码是相互的，可以互为反码  
补码：反码+1得补码

###  6.5. <a name='-1'></a>赋值运算符  

|运算符|描述|
|:-:|:-:|
|=|简单的赋值运算符，把右边操作数的值赋给左边操作数|
|+=|加且赋值运算符，把右边操作数加上左边操作数的结果赋值给左边操作数|
|-=|减且赋值运算符，把左边操作数减去右边操作数的结果赋值给左边操作数|
|*=|乘且赋值运算符，把右边操作数乘以左边操作数的结果赋值给左边操作数|
|/=|除且赋值运算符，把左边操作数除以右边操作数的结果赋值给左边操作数|
|%=|求模且赋值运算符，求两个操作数的模赋值给左边操作数|
|<<=|左移且赋值运算符|
|>>=|右移且赋值运算符|
|&=|按位与且赋值运算符|
|^=|按位异或且赋值运算符|
|\|=|按位或且赋值运算符|


###  6.6. <a name='sizeof'></a>杂项运算符  sizeof & 三元  

|运算符|描述|
|:-:|:-:|
|sizeof()||
|&|返回变量的大小|
|*|返回变量的地址|
|?:|条件表达式|

```c 
Exp1 ? Exp2 : Exp3;
```
Exp1,2,3都是表达式 
Exp1 为真 就计算 Exp2的值 ，反之计算 Exp3的值  
![](https://kogasaimgbed.oss-cn-beijing.aliyuncs.com/noteimgs/20220604164831.png)



###  6.7. <a name='C-1'></a>C 中的运算符优先级

初等运算符>单目运算符>算术运算符>关系运算符>逻辑运算符>条件运算符>赋值运算符  

##  7. <a name='C-1'></a>C 判断 

###  7.1. <a name='if'></a>if 语句
> 单if语句 
```c 
if (boolean_expression)
{
    /*如果布尔表达式为真将执行语句*/
}
```

> if...else 语句 

```c
if (boolean_expression)
{
    /*如果布尔表达式为真将执行的语句*/
}
else
{
    /*如果布尔表达式为假将执行的语句*/
}
```

> if...else if...else 语句  

```c
if(boolean_expression 1)
{
    /*当布尔表达式 1 为真时执行*/
}
else if(boolean_expression 2)
{
    /*当布尔表达式 2 为真时执行*/
}
else if(boolean_expression 3)
{
    /*当布尔表达式 3 为真时执行*/
}
else
{
    /*当上面条件都不为真时执行*/
}
```
>嵌套 if 语句

```c
if(boolean_expression 1)
{
    /*当布尔表达式 1 为真时执行*/
    if(boolean_expression 2)
    {
        /*当布尔表达式 2 为真时执行*/
    }
}
```

###  7.2. <a name='switch'></a>switch 语句 

>单一 switch

```c
switch(expression){
    case constant-expression :
        statement(s);
        break;//可选
    case constant-expression :
        statement(s);
        break;//可选
    
    /*可以使用任意数量的case语句*/
    default : //可选
        statement(s);
}
```

+ switch 语句中的 expression 是一个常量表达式，必须是一个整型或枚举类型
+ 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号
+ case 的 constant-expression 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量或字面量
+ 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 break 语句为止 
+ 当遇到 break 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行 
+ 不是每一个 case 都需要包含 break。如果 case 语句不包含 break，控制流将会 继续 后续的 case，直到遇到 break 为止 
+ 一个 switch 语句可以有一个可选的 default case，出现在 switch 的结尾。default case 可用于在上面所有 case 都不为真时执行一个任务。default case 中的 break 语句不是必需的


> 嵌套 switch 语句 

```c 
switch(ch1) {
    case 'A':
        printf("这个A 是外部switch的一部分");
        switch(ch2) {
            case 'A': 
                printf("这个A是内部switch的一部分");
                break;
            case 'B' : /*内部B case的代码*/    
        }
        break;
    case 'B' : /*外部B case 代码*/
}
```

##  8. <a name='C-1'></a>C 循环 

###  8.1. <a name='-1'></a>循环类型 
> while循环 
当给定条件为真时，重复语句或语句组。从而重复执行循环主体之前的测试条件 
```c
while(condition)
{
    statement(s);
}
```
statement(s)可以是一个单独的语句。也可以是几个语句组成的代码块  
condition可以是任意的表达式，任意非0值为true，并执行循环 
false时，退出循环接下来执行下一条语句  

>for 循环

```c
for (init ; condition ; increment)
{
    statement(s);
}

```
init被首先执行 ，声明并初始化控制变量，也可以只写一个分号 
接下来判断condition , 如果为真，执行循环主体；如果为假，则不执行。跳转到for循环的下一个语句  
执行for循环主体之后，控制流回到 increment 。进而更新循环控制变量，也可以留空  

> do...while 循环 

```c
do
{
    statement(s);

}while(condition);
```

循环中的statement(s)至少会被执行一次 ，如果条件为真，控制流程会回到do，然后重新执行
知道条件变为假为止  

###  8.2. <a name='-1'></a>循环控制语句

> break 语句

+ 当break语句出现在一个循环当中时，循环会立即终止，然后继续执行循环的下一条语句 
+ 可以用于终止switch语句的一个case
+ 如果是用于嵌套循环，break可以终止最最内层的循环，然后执行该块之后的下一行代码 

> continue 语句

+ continue 可以跳过当前循环的代码，强制开始下一次循环 
+ 在for循环中，continue之后的自增语句依然会执行
+ while和do...while语句中，continue语句会重新执行条件判断语句 

> goto 语句

goto语句允许把控制无条件转移到同一函数内的被标记的语句  
不推荐使用 
```c
goto label;
//略


label:statement;

```

> 无限循环  

```c
#include <stdio.h>

int main()
{
    for(;;)
    {
        printf("停不下来！\n");
    }
    return 0;
}

使用 Ctrl + C 来终止一个无限循环  

```
##  9. <a name='C-1'></a>C 函数

定义:  
```c
return_type function_name( parameter list )
{
    body of the function
}
```

+ return_type 返回类型 。每个函数可以返回一个值，这个类型代表着返回值的数据类型 
    如果有些函数不需要返回值，则关键字是void  
+ function_name 函数名称  函数的实际名称 ，其和参数列表一起构成函数签名  
+ parameter list 参数  参数类似与占位符，当函数被调用，我们向参数传递一个值，这个值被称之为实际参数 
    参数列表包括函数的类型、顺序、数量。并且可以不包含参数  
+ body of the function  函数主体  一组定义函数执行的语句  

###  9.1. <a name='-1'></a>函数声明  

函数声明会告诉编译器函数名称以及如何调用函数，函数主体可以单独定义  
包括以下几个部分  
```c
return_type function_name( parameter list);
```
在函数声明中，参数的名称并不重要，只有参数的类型是必需的
```c
int max(int,int);
```
这种格式也是可以的  

###  9.2. <a name='-1'></a>调用函数  

创建C函数时，可以定义函数做什么，然后通过函数来完成定义的任务   
当程序调用函数，程序控制会转移到被调用的函数 。被调用的函数完成之后，将程序控制还给主程序  
例子： 
```c
#include <stdio.h>
/*声明函数*/
int max(int num1,int num2);

int main()
{
    /*局部变量定义*/
    int a = 100;
    int b = 200;
    int ret;

    /*调用函数来获取最大值*/
    ret = max(a,b);

    printf("Max value is : %d\n",ret);

    return 0;
}

/*函数返回两个数中较大的那个数*/
int max(int num1,int num2)
{
    /*局部变量声明*/
    int result;

    if(num1 > num2)
        result = num1;
    else
        result = num2;

    return result;
}
```

###  9.3. <a name='-1'></a>函数参数  

函数使用参数，必须声明接受参数值的变量，这些变量称之为形式参数  
形参在进入函数时被创建，退出函数时被销毁  
主要有两种向函数传递参数的方式  
传值调用：
+ 把参数的实际值复制给函数的形参  
+ 修改函数内的形参不会影响实际参数  
引用调用： 
+ 形参指向实参地址的指针
+ 对形参的指向操作等于对参数本身的操作  
+ 传递指针可以让多个函数访问指针所引用的对象，而不需要把对象声明为全局可见   

> 关于形参与实参
实参可以是变量，变量与表达式 

实参与形参类型相同或赋值兼容 
在调用函数过程中发生的实参与形参之间的数据传递，常称为"虚实结合"

+ 在定义函数中制定的形参，在没有出现函数调用时不占用内存中的存储单元。在函数调用时才分配内存  
+ 在执行函数时，由于形参已经有值。可以用形参进行运算 
+ 通过return语句将函数值返回，若无返回值，则无return
+ 调用结束后，形参被释放掉，实参保留原值（单向传值）

###  9.4. <a name='-1'></a>占位符
占位符用于占有一个固定未知，再往里面添加内容，主要用于计算机中各类文档的编辑  

+ %d,%i 代表整数
+ %f 浮点
+ %s 字符串
+ %c char
+ %p 指针
+ %fL 长log
+ %e 科学计数
+ %g 小数或者科学计数 
+ %a,%A 读入一个浮点值（C99）
+ %c 读入一个字符 
+ %d 读入十进制整数 
+ %i 读入十进制，八进制，十六进制整数 
+ %o 读入八进制整数 
+ %x，%X 读入十六进制整数  
+ %s 读入一个字符串，遇到空格、制表符或换行时结束  
+ %f,%F,%e,%E,%g,%G 输入实数，可以用小数形式或指数形式输入  
+ %p 读入一个指针 
+ %u 读入一个无符号十进制整数 
+ %n 至此已读入值的等价字符数 
+ %[] 扫描字符合集 
+ %% 读 % 符号

##  10. <a name='-1'></a>作用域规则  

可以声明变量的三个地方：
+ 在函数内部或块内部的局部变量
+ 在所有函数外部的全局变量
+ 在形式参数的函数参数定义中
  
###  10.1. <a name='-1'></a>局部变量

声明在某个函数或块的内部的变量称之为局部变量 
只能被该函数或代码块内部的语句使用，在函数外部不可知  

###  10.2. <a name='-1'></a>全局变量  

全局变量定义在函数外部，通常在程序的顶部  
在整个程序的声明周期都是有效的，任意的函数都能访问 
在程序中，如果局部变量和全局变量的名称相同，优先使用局部变量  

###  10.3. <a name='-1'></a>形式参数 

函数的参数，形式参数。被当作函数内的局部变量 
与全局变量重名会优先调用  

```c
#include <stdio.h>

/*全局变量声明*/
int a = 20;

int main()
{
    /*在主函数中的局部变量声明*/
    int a = 10;
    int b = 20;
    int c = 0;
    int sum(int,int);

    printf("value of a in main() = %d\n", a);
    c = sum(a,b);
    printf("value of a in main() = %d\n",c);

    return 0;
}

/*添加两个整数的函数*/
int sum(int a,int b)
{
    printf("value of a in sum() = %d\n",a);
    printf("value of a in sum() = %d\n",b);

    return a + b;
}

```

###  10.4. <a name='-1'></a>初始化局部变量和全局变量  

局部变量不会被系统自动初始化，全局变量会被自动初始化  
|数据类型|初始化默认值|
|:-:|:-:|
|int|0|
|char|'\0'|
|float|0|
|double|0|
|pointer|NULL|

##  11. <a name='-1'></a>数组 

数组是用来存储一系列数据，一般是被认为一系列相同类型的变量  
C语言可以存储一个固定大小的类型相同元素的顺序组合  

###  11.1. <a name='-1'></a>声明数组 
```c
type arrayName [arraySize];
```
这个称之为一维数组。arraySize必须是一个大于0的整数常量  
type可以是任意有效的C数据类型  
例如：声明一个类型为 double 的包含 10 个元素的数组 balance
```c
double balance[10];
```
这个数组可以容纳10个类型为double的数字  

###  11.2. <a name='-1'></a>初始化数组  

使用类似于以下的结构进行初始化  

```c
double balance[4] = {1,1,4,5,1,4};
```

{ }之间的数值的数目不能超过[ ]中声明的元素个数  
可以选择[ ]内留空,然后进行数组的初始化  

```c
double balance[] = {1,1,4,5,1,4,1,9,1,9,8,1,0};
```

注意：
+ 数组的索引是从0开始的，第一个元素的索引称之为基索引 
+ 数组的最后一个索引是数组的总大小-1
+ [8]代表索引为8,但是是第9个元素 

###  11.3. <a name='-1'></a>访问数组元素 

可以通过数组名称加索引进行访问，例如：

```c
double xianbei = balance[9];
```

##  12. <a name='enum'></a>enum(枚举)

枚举是一种数据类型，让数据更简洁，易读  
定义格式:
```c
enum 枚举名 {元素1,元素2,....};
```

###  12.1. <a name='-1'></a>枚举变量的定义 
定义枚举变量的三种方式: 
+ 先定义枚举类型，再定义枚举变量
```c
enum DAY
{
    MON=1,TUE,WED,THD,FRI,SAT,SUN
};
enum DAY day;
```
+ 定义枚举类型的同时定义枚举变量
```c
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;
```
+ 省略枚举名称，直接定义枚举变量 
```c
enum
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;
```
在 C 语言中，枚举类型是被当做 int 或者 unsigned int 类型来处理的，所以按照 C 语言规范是没有办法遍历枚举类型的  

例子：  
```c

#include <stdio.h>
 
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
};
 
int main()
{
    enum DAY day;
    day = WED;
    printf("%d",day);
    return 0;
}
//输出结果为：3
```

