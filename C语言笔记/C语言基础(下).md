<!-- vscode-markdown-toc -->
* 1. [指针](#)
	* 1.1. [指针定义](#-1)
	* 1.2. [指针使用](#-1)
	* 1.3. [NULL指针](#NULL)
	* 1.4. [指针的算数运算](#-1)
	* 1.5. [指针数组](#-1)
	* 1.6. [指针数组和数组指针的区别](#-1)
	* 1.7. [指向指针的指针](#-1)
	* 1.8. [传递指针给函数](#-1)
	* 1.9. [从函数返回指针](#-1)
	* 1.10. [复杂指针的说明](#-1)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

# C语言基础(下)

##  1. <a name=''></a>指针 
指针可以简化一些C编程任务的执行，实现动态内存分配 
由于每一个变量都有一个内存位置，每一个内存位置都定义了可使用 & 运算符访问的地址，表示了在内存中的一个地址  

例如：
```c
#include <stdio.h>

int main()
{
    int kogasa = 10;
    int *p; //定义指针变量 
    p = &kogasa;

    printf("kogasa 变量的地址： %p\n",p);
    return 0;
}
```

###  1.1. <a name='-1'></a>指针定义
指针也就是内存地址，指针变量存储着内存地址的变量 
在使用指针之前，使用这样的格式预先进行声明： 
```c
type *var_name;
```
type是指针的类型，必须是有效的c类型。var_name是指针变量的名称  
指针的类型必须与变量 var_name的类型一直
所有实际数据类型，指针值的类型都是代表内存地址的长十六进制数  

###  1.2. <a name='-1'></a>指针使用

一般以下操作会频繁进行：
+ 定义一个指针变量 
+ 把变量地址赋值给指针 
+ 访问指针变量中可用地址的值  

一般通过 * 一元运算符来返回位于操作数所指定地址的变量的值  

```c
#include <stdio.h>

int main()
{
    int var = 20; /*实际变量的声明*/
    int *ip;      /*指针变量的声明*/

    ip = &var; /*在指针变量中存储var的地址*/

    printf("var 变量的地址： %p\n",&var);

    /*在指针变量中存储的地址*/
    printf("ip 变量存储的地址：%p\n",ip);

    /*使用指针访问值*/
    printf("*ip 变量的值：%d\n",*ip);
}
```

###  1.3. <a name='NULL'></a>NULL指针  

声明变量的时候，如果没有确切的可以赋值的地址，可以为指针变量赋一个NULL  
被赋予NULL值的指针被称之为空指针  

例如：
```c
#include <stdio.h>

int main()
{
    int *ptr = NULL;
    printf("ptr的地址是%p\n",ptr);
    return 0;
}
```

###  1.4. <a name='-1'></a>指针的算数运算

我们可以对指针进行四种算数运算： ++，--，+，-  

+ 指针每一次递增，会指向下一个元素的存储单元
+ 指针每一次递减，会指向前一个元素的存储单元 
+ 指针在递增和递减时跳跃的字节数取决于指针所指向数据类型长度  
  + 例如：int是4个字节 

> 递增一个指针 
例：用递增变量指针来顺序访问数组中的每一个元素  ‘

```c
#include <stdio.h>

const int MAX = 3;

int main()
{
    int var[] = {10,100,200};
    int i,*ptr;

    /*指针中的数组地址*/
    ptr = var;
    for (i = 0;i < MAX;i++)
    {
        printf("存储地址：var[%d] = %p\n",i,ptr);
        printf("存储值：var[%d] = %d\n",i,*ptr);

        /*指向下个位置*/
        ptr++;
    }
    return 0;
}
```
本次运行的结果为：
```
存储地址：var[0] = 0x7ffea513da4c
存储值：var[0] = 10
存储地址：var[1] = 0x7ffea513da50
存储值：var[1] = 100
存储地址：var[2] = 0x7ffea513da54
存储值：var[2] = 200
```
> 递减一个指针  
例：
```c
#include <stdio.h>
 
const int MAX = 3;
 
int main ()
{
   int  var[] = {10, 100, 200};
   int  i, *ptr;
 
   /* 指针中最后一个元素的地址 */
   ptr = &var[MAX-1];
   for ( i = MAX; i > 0; i--)
   {
 
      printf("存储地址：var[%d] = %p\n", i-1, ptr );
      printf("存储值：var[%d] = %d\n", i-1, *ptr );
 
      /* 指向下一个位置 */
      ptr--;
   }
   return 0;
}
```

本次运行的结果为：
```
存储地址：var[2] = 0x7ffcf50a2014
存储值：var[2] = 200
存储地址：var[1] = 0x7ffcf50a2010
存储值：var[1] = 100
存储地址：var[0] = 0x7ffcf50a200c
存储值：var[0] = 10

```

> 指针的比较  

指针可以用关系运算符进行比较，如==，<,>  
如果p1和p2指向两个相关的变量，比如同一个数组中的不同元素，就可以对p1和p2进行大小比较  

例：只要指针变量所指向的地址小于或等于数组的最后一个元素的地址&var[MAX-1],就把指针变量进行递增  
```c
#include <stdio.h>

const int MAX = 3;

int main()
{
    int var[] = {10,100,200};
    int i,*ptr;

    /*指针中第一个元素的地址*/
    ptr = var;
    i = 0;
    while (ptr <= &var[MAX-1])
    {

        printf("存储地址：var[%d] = %p\n",i,ptr);
        printf("存储值：var[%d] = %d\n",i,*ptr);

        /*指向上一个位置*/
        ptr++;
        i++;
    }
    return 0;
}
```
运行结果如下：

```
存储地址：var[0] = 0x7ffeb81cdc9c
存储值：var[0] = 10
存储地址：var[1] = 0x7ffeb81cdca0
存储值：var[1] = 100
存储地址：var[2] = 0x7ffeb81cdca4
存储值：var[2] = 200
```

###  1.5. <a name='-1'></a>指针数组  

当我们想让数组存储指向int或者char或者其他数据类型的指针，可以尝试类似于以下的结构：
```c
int *ptr[MAX]
```
这里可以表示由MAX个整数指针组成。每个ptr中的元素都是一个指向int值的指针  
同样，我们也可以用一个指向字符的指针数组来存储一个字符串列表  
```c
#include <stdio.h>

const int MAX = 4;

int main()
{
    const char *names[]= {
            "Lunasa Prismriver!",
            "Merlin Prismriver!",
            "Lyrica Prismriver!",
            "Leira Prismriver!"
    };
    int i = 0;

    for(i = 0;i < MAX;i++)
    {
        printf("Value of names[%d] = %s\n",i,names[i]);
    }
    return 0;

}
```
运行结果如下：
```c
Value of names[0] = Lunasa Prismriver!
Value of names[1] = Merlin Prismriver!
Value of names[2] = Lyrica Prismriver!
Value of names[3] = Leira Prismriver!
```

###  1.6. <a name='-1'></a>指针数组和数组指针的区别

> 指针数组
+ 首先这是一个数组，“指针的数组” 
+ 意思是这个数组的所有元素都是指针类型 
+ int *p1[3];

> 数组指针  
+ 这是一个指针，“数组的指针”
+ 这个指针指向一个数组的首地址
+ int (*p2)[3];  

###  1.7. <a name='-1'></a>指向指针的指针 

这是一种多级简介寻址的形式，或称之为一个指针链。  
一个指针包含了一个变量的地址  
当定义了一个指针的指针时，第一个指针包含了第二个指针的地址，第二个指针包含实际值的地址  
例子：int类型指针的指针  
```c
int **var;
```

###  1.8. <a name='-1'></a>传递指针给函数 

函数的参数类型可以声明为指针  
能接受指针作为参数的函数，也能接受数组作为参数 
+ 例1
```c
#include <stdio.h>
#include <time.h>

void getSeconds(unsigned long *par);

int main()
{
    unsigned long sec;

    getSeconds( &sec );

    /*输出实际值*/
    printf("Number of seconds: %d\n", sec);

    return 0;
}

void getSeconds(unsigned long *par)
{
    /*获取当前的秒数*/
    *par = time(NULL);
    return;
}
```
运行结果：
```c
Number of seconds: 1654648611
```

例2：
```c
#include <stdio.h>

/*函数声明*/
double getAverage(int *arr,int size);

int main()
{
    /*带有5个元素的整型数组*/
    int balance[5] = {114,514,19,19,810};
    double avg;

    /*传递一个指向数组的指针作为参数*/
    avg = getAverage( balance,5);

    /*输出返回值*/
    printf("Average value is: %f\n",avg);

    return 0;
}

double getAverage(int *arr,int size)
{
    int i,sum=0;
    double avg;

    for(i = 0; i < size;++i)
    {
        sum += arr[i];
    }

    avg = (double)sum /size;

    return avg;
}
```
运行结果：
```
Average value is: 295.200000
```

###  1.9. <a name='-1'></a>从函数返回指针  

C允许从函数返回指针  
可以用如下的格式声明一个返回指针的函数  
```c
int *myFunction()
{
    ...
}
```

C不支持在调用函数时返回局部变量的地址，除非局部变量是static的  

###  1.10. <a name='-1'></a>复杂指针的说明  

+ int p;  普通的整型变量  
+ int *p;  一个返回整型数据的指针  
+ int p[3];  一个由整型数据组成的数组  
+ int *p[3]; 一个由返回整型数据的指针所组成的数组 
+ int (*p)[3]; 一个指向由整型数据组成的数组的指针 
+ int **p; 一个指向整型元素指针的指针
+ int p(int);  一个有整型变量的参数，返回值是整型数据的函数 
+ int (*p)(int); 一个指向有一个整型参数且返回类型为整型的函数的指针  
+ int *(*p(int))[3]; 一个参数为整型且返回指向一个由整型指针变量组成的数组的指针变量的函数  
  
