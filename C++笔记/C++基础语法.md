
# C++基础语法 

## 从Hello，world！开始
第一个程序

```c++
#include <iostream>  //预处理器

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

另外一则实例
```c++
#include <iostream>

int main() {
    using namespace std; //在开头声明名称空间，后面就只需要使用cout
    cout << "Kogasa_Touhou!";
    cout << endl;
    cout << "WULA!" << endl;
    return 0;
}
```
二者是等价的 
std是名称空间 ，::是作用域运算符，cout是std空间的一个函数名  
使用cout函数必须有std名称空间的说明  

> main()函数  

main()函数的基本结构：
```c++
int main()  //函数头
{    //函数体 
    statements    
    return 0;  //结束函数  
}
```
注意事项:   
+ 一个常规独立程序必定有main()函数 
+ 以下两种参数方式等效 
  + int main(void)
  + int main() 
+ 也可以使用以下函数头，同时省略返回语句 
  + void main()


> 注释 

使用与C语言相同的注释方式 
```c++
//单行注释
/*
多行注释
多行注释
*/
```

> 名称空间  

名称空间是C++的一项特性，可以用于区分不同封装产品的同名函数。 
```c++
Kogasa::wula("wula!!!!");//小伞名称空间的版本
Cccp::wula("wula!!!!"); //气突苏名称空间的版本 
```

提前使用using指令来表明指定的名称空间的函数，从而避免使用前缀  
```c++
using namespace std;  //使得std名称空间中的所有名称都可以使用

using std::cout; 
using std::endl;
using std::cin;// 使得指定的名称可以使用 
```


> 使用cout输出  

例子里已经体现了如何使消息输出  
<<  符号是插入运算符 ，并不是c语言中的左移  
使用如下的方式，将符号右侧的信息插入信息流之中
```c++
cout << String;
```

从上面的例子也看出了，cout是支持拼接的，会自动合并成一条长的语句  


> 控制符 endl  

其含义是在输出流中插入endl使得屏幕光标移动到下一行的开头   
cout不会自动换行，搭配使用endl达成换行的效果  

C++同样也支持换行符  
```c++
cout << "what's up ! \n";    
```
其效果和 << endl等价  

使用这两种方式都可以做到空行的效果  
```c++
cout << "\n";
cout << endl;
```
不用按shift的感觉还是比较nice的（不是） 

## C++语句  

例子1：
```c++
#include <iostream>

int main() {
    using namespace std;

    int coins; //声明coins变量   

    coins = 2; //赋值语句 
    cout << "Reimu has ";
    cout << coins;  //用于打印变量 
    cout << " coins in her pocket." << endl;
    coins -= 2;  //coins = coins -2 ;
    cout << "Marisa passed by,now Reimu has " << coins << " coins. (Lmao)" << endl;
    return 0;
}

```
输出结果：
```shell
Reimu has 2 coins in her pocket.
Marisa passed by,now Reimu has 0 coins. (Lmao)
```

所有C++变量在首次使用之前必须进行声明  
= 是赋值符号，支持连续赋值  

kogasa = reimu = marisa = 1;

首先，1被赋值给marisa,然后是reimu,最后是kogasa  

例子2：  
```c++
#include <iostream>

int main() {
    using namespace std;

    int coins;

    cout << "How many coins do you have?" << endl;
    cin >> coins; //从键盘键入数值并赋值给coins变量  
    cout << "Here are two more.";
    coins += 2;
    cout << "Now you have " << coins << " coins." << endl;
    return 0;
}
```
<< 和 >> 被用来指示信息流的方向  
 
## 变量  
> 命名规则  

+ 名称中只能使用大小写字母、数字和下划线  
+ 不能以数字开头  
+ 区分大小写  
+ 不能使用关键字  
+ 对于名称长度没有限制，但是有些平台会有所限制  
+ 以两个下划线或下划线+大写字母打头的名称被保留给实现（编译器及其使用的资源）使用  
+ 以一个下划线开头的名称被保留给实现，用作全局标识符  
+ 命名最好做到见名之意  

> 基本内置数据类型  

|类型|关键字|
|:-:|:-:|
|布尔型|bool|
|字符型|char|
|整型|int|
|浮点型|float|
|双浮点型|double|
|无类型|void|
|宽字符型|wchar_t|

> 不同类型的范围  

|类型|位(字节)|范围|
|:-:|:-:|:-:|
|char|1|-128 到 127 或者 0 到 255|
|unsighed char|1|0 到 255|
|signed char|1|-128 到 127|
|int|4|-2147483648 到 2147483647|
|unsigned int|4|0 到 4294967295|
|signed int|4|-2147483648 到 2147483647|
|short int|2|-32768 到 32767|
|unsigned short int|2|0 到 65,535|
|signed short int|2|-32768 到 32767|
|long int|8|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|
|signed long int|8|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|
|unsigned long int|8|0 到 18,446,744,073,709,551,615|
|float|4|精度型占4个字节（32位）内存空间，+/- 3.4e +/- 38 (~7 个数字)|
|double|8|双精度型占8 个字节（64位）内存空间，+/- 1.7e +/- 308 (~15 个数字)|
|long double|16|长双精度型 16 个字节（128位）内存空间，可提供18-19位有效数字|
|wchar_t|2,4|1个宽字符|



