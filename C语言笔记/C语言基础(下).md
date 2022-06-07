<!-- TOC -->

- [C语言基础下](#c%E8%AF%AD%E8%A8%80%E5%9F%BA%E7%A1%80%E4%B8%8B)
    - [指针](#%E6%8C%87%E9%92%88)
        - [指针定义](#%E6%8C%87%E9%92%88%E5%AE%9A%E4%B9%89)
        - [指针使用](#%E6%8C%87%E9%92%88%E4%BD%BF%E7%94%A8)
        - [NULL指针](#null%E6%8C%87%E9%92%88)
        - [指针的算数运算](#%E6%8C%87%E9%92%88%E7%9A%84%E7%AE%97%E6%95%B0%E8%BF%90%E7%AE%97)
        - [指针数组](#%E6%8C%87%E9%92%88%E6%95%B0%E7%BB%84)

<!-- /TOC -->

# C语言基础(下)

## 指针 
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

### 指针定义
指针也就是内存地址，指针变量存储着内存地址的变量 
在使用指针之前，使用这样的格式预先进行声明： 
```c
type *var_name;
```
type是指针的类型，必须是有效的c类型。var_name是指针变量的名称  
指针的类型必须与变量 var_name的类型一直
所有实际数据类型，指针值的类型都是代表内存地址的长十六进制数  

### 指针使用

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

### NULL指针  

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

### 指针的算数运算

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

### 指针数组  

