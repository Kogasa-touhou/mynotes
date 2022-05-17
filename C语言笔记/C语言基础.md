[Toc]
# C语言基础  

## 主要结构  

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
### 编译&运行C程序  
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

## 基础语法  

### C的令牌（Token）

C语言由各种令牌组，可以是关键字、标识符、常量、字符串、符号等。
例如:  
```c
printf("Hello World!"\n);
```

令牌分别是: printf  (   "Hello World!"\n    )    ;      五个


### 分号 ;

分号代表着语句的结束，表明一个逻辑实体的结束
请不要写成中文的分号  

### 注释  

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

### 标识符  

C语言的标识符用来标识变量、函数，或者任何其他用户自定义项目的名称。
以A-Z，a-z，下划线_开始，后接0个或者多个字母、下划线和数字(0-9)  
区分大小写  
标识符内不允许出现标点字符(@ $ %等)

### 关键字  

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

### C中的空格 

空行会被编译器忽视  
空格用于描述空白符、制表符、换行符以及注释  
```c
people = man + woman
```
这几个之间的空格不是必要的但是为了增加可读性，可以适当添加  

## C数据类型  
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

