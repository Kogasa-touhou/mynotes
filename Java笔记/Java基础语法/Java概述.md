# 我的第一个Java程序 

```java
//文件名 Test.java
public class Test{
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

+ Java源文件是以".java"为扩展名的，其基本组成部分是类(class)  
+ Java应用程序的执行入口是main()方法，其固定格式是：
  + public static void main(String[] args) {...}
+ 注意严格区分大小写 
+ 语句由一条条语句构成，每个语句以";"结束  
+ 大括号成对出现  
+ 一个源文件最多只能有public类，其他类的个数不限 
+ 包含public类的源文件必须以这个类的名字命名  
  
## 关于注释  
+ 用于注释说明解释程序的文字就是注释  
+ Java中的注释类型 
  + 单行注释
  + 多行注释
  + 文档注释
+ 写注释可以提高代码的阅读性，是调试的重要方法  
+ 写注释是好文明建议提倡  
+ 学会用注释去整理自己的思想  

### 注释案例  
+ 单行注释 
> 格式   

```java
//注释文字
```

+ 多行注释 
> 格式  

```java
/*
注释
文字
*/
```

+ 注意：
  + 被注释的文字不能被JVM所执行  
  + 多行注释里不允许有多行注释嵌套  

+ 文档注释 (Java特色)
> 格式  
```java
/**
@author 指定java程序的作者
@version 指定源文件的版本
*/
```
注释内容被jdk提供的javadoc解析，生成一套网页文件形式的该程序的说明文档  
> 操作方式  
```shell
javadoc -d mydoc -author -version HelloWorld.java
```