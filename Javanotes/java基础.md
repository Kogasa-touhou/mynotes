[Toc]
# java基础笔记
## 第一个java程序

## 第一个java程序
>创建文件HelloWorld.java(文件名字与类名一致)
```java
public static void main(String[] args){
    System.out.println("Hello World");
}
```
+ 注意: __String args[]__与__String[] args__都可以执行，但是推荐使用__String[] args__,可以避免歧义和误读。  
>关于args  
>> 运行如下代码  
```
public class Test {
    public static void main(String[] args) {
        System.out.println(args[0]);
    }
}
```  
```
$ javac Test.java
$ java Test runoob
runoob
```  
+ 此处注意，main 是一个程序的入口，一个 java 程序运行必须而且有且仅有一个 main 方法。args[0] 是你传入的第一个参数，args[1]是传入的第二个参数，以此类推。
+ __Sring[] args__ 还有一种等价写法： __String... args__  
前者为数组形式, 后者为可变参数形式。  
前者用得较多, 但是看到后者也应认识。

+ Java 程序利用 main 函数中 args 参数实现参数的传递(__传递空格处理__)
```java
public class Test
{
    public static void main(String []args)
    {
        System.out.println(args[0]);
        System.out.println(args[1]);
        System.out.println(args[2]);
    }
}
```
> 运行  
```shell
$ javac Test.java
$ java Test aaa bbb ccc 
aaa
bbb
ccc
```
注意：三个参数之间用空格隔开！  
如果要输出空格怎么办？  
只需要在包含空格的参数上，使用双引号 "" 即可。  
>实例运行：  
```shell
$ java Test aaa "b   bb" ccc
aaa
b   bb
ccc
```


>运行
```shell
$ javac HelloWorld.java
$ java HelloWorld
Hello World
```
>执行命令解析  

+ __javac__ 后面跟着的是java文件的文件名(xxx.java).该命令用于将 java 源文件编译为 class 字节码文件，如： __javac HelloWorld.java__ 
+ 该命令用于将 java 源文件编译为 class 字节码文件，如： javac HelloWorld.java
+ __java__ 后面跟着的是java文件中的类名,例如 HelloWorld 就是类名，如: java HelloWorld
+ __注意__：java命令后面不要加.class  

## Java 基础语法
一个 Java 程序可以认为是一系列对象的集合，而这些对象通过调用彼此的方法来协同工作。下面简要介绍下类、对象、方法和实例变量的概念  
+ __对象__：对象是类的一个实例，有状态和行为。例如，一条狗是一个对象，它的状态有：颜色、名字、品种；行为有：摇尾巴、叫、吃等  
+ __类__：类是一个模板，它描述一类对象的行为和状态
+ __方法__：方法就是行为，一个类可以有很多方法。逻辑运算、数据修改以及所有动作都是在方法中完成的  
+ __实例变量__：每个对象都有独特的实例变量，对象的状态由这些实例变量的值决定  

> 程序实例
```java
public class HelloWorld {
    /* 第一个Java程序
     * 它将输出字符串 Hello World
     */
    public static void main(String[] args) {
        System.out.println("Hello World"); // 输出 Hello World
    }
}
```
![20211218134628-2021-12-18-13-46-28](http://kogasaimgbed.oss-cn-beijing.aliyuncs.com/noteimgs/20211218134628-2021-12-18-13-46-28.png)

+ 如果遇到编码问题，我们可以使用 -encoding 选项设置 utf-8 来编译： 
```shell
javac -encoding UTF-8 HelloWorld.java 
java HelloWorld 
```

## 基本语法  
编写java程序的时候，应该注意以下几点：
+ __大小写敏感__：Java 是大小写敏感的，这就意味着标识符 Hello 与 hello 是不同的
+ __类名__：对于所有的类来说，类名的首字母应该大写。如果类名由若干单词组成，那么每个单词的首字母应该大写，例如 MyFirstJavaClass 
+ __方法名__：所有的方法名都应该以小写字母开头。如果方法名含有若干单词，则后面的每个单词首字母大写
+ __源文件名__：源文件名必须和类名相同。当保存文件的时候，你应该使用类名作为文件名保存（切记 Java 是大小写敏感的），文件名的后缀为 .java。（如果文件名和类名不相同则会导致编译错误）
+ __主方法入口__：所有的 Java 程序由 public static void main(String[] args) 方法开始执行

## Java标识符  

Java 所有的组成部分都需要名字。类名、变量名以及方法名都被称为标识符  
关于 Java 标识符，有以下几点需要注意：  
+ 所有的标识符都应该以字母（A-Z 或者 a-z）,美元符（$）、或者下划线（_）开始
+ 首字符之后可以是字母（A-Z 或者 a-z）,美元符（$）、下划线（_）或数字的任何字符组合
+ 关键字不能用作标识符
+ 标识符是大小写敏感的
+ 合法标识符举例：age、$salary、_value、__1_value
+ 非法标识符举例：123abc、-salary

## Java修饰符  

像其他语言一样，Java可以使用修饰符来修饰类中方法和属性。主要有两类修饰符：  
+ 访问控制修饰符 : default, public , protected, private
+ 非访问控制修饰符 : final, abstract, static, synchronized

## Java变量

Java 中主要有如下几种类型的变量
+ 局部变量
+ 类变量（静态变量）
+ 成员变量（非静态变量）

## Java数组


## Java枚举

Java 5.0引入了枚举，枚举限制变量只能是预先设定好的值。使用枚举可以减少代码中的 bug。  
例如，我们为果汁店设计一个程序，它将限制果汁为小杯、中杯、大杯。这就意味着它不允许顾客点除了这三种尺寸外的果汁。  
__实例__
```java
class FreshJuice {
   enum FreshJuiceSize{ SMALL, MEDIUM , LARGE }
   FreshJuiceSize size;
}
 
public class FreshJuiceTest {
   public static void main(String[] args){
      FreshJuice juice = new FreshJuice();
      juice.size = FreshJuice.FreshJuiceSize.MEDIUM  ;
   }
}
```
__注意__：枚举可以单独声明或者声明在类里面。方法、变量、构造函数也可以在枚举中定义。  

## Java关键字
<table>
    <tr>
        <th>类别</th>
        <th>关键字</th>
        <th>说明</th>
    </tr>
    <tr>
        <td rowspan="4">访问控制</td>
        <td>private</td>
        <td>私有的</td>
    </tr>
    <tr>
        <td>protected</td>
        <td>受保护的</td>
    </tr>
    <tr>
        <td>public</td>
        <td>公共的</td>
    </tr>
    <tr>
        <td>default</td>
        <td>默认</td>
    </tr>
    <tr>
        <td rowspan="13">类、方法和变量修饰符</td>
        <td>abstract</td>
        <td>声明抽象</td>
    </tr>
    <tr>
        <td>class</td>
        <td>类</td>
    </tr>
    <tr>
        <td>extends</td>
        <td>扩充，继承</td>
    </tr>
    <tr>
        <td>final</td>
        <td>最终值，不可改变的</td>
    </tr>
    <tr>
        <td>implements</td>
        <td>实现(接口)</td>
    </tr>
    <tr>
        <td>interface</td>
        <td>实现(接口)</td>
    </tr>
    <tr>
        <td>native</td>
        <td>本地，原生方法(非 Java 实现)</td>
    </tr>
    <tr>
        <td>new</td>
        <td>新，创建</td>
    </tr>
    <tr>
        <td>static</td>
        <td>静态</td>
    </tr>
    <tr>
        <td>strictfp</td>
        <td>严格，精准</td>
    </tr>
    <tr>
        <td>synchronized</td>
        <td>线程，同步</td>
    </tr>
    <tr>
        <td>transient</td>
        <td>短暂</td>
    </tr>
    <tr>
        <td>volatile</td>
        <td>易失</td>
    </tr>
    <tr>
        <td rowspan="12">程序控制语句</td>
        <td>break</td>
        <td>跳出循环</td>
    </tr>
    <tr>
        <td>case</td>
        <td>定义一个值以供switch选择</td>
    </tr>
    <tr>
        <td>continue</td>
        <td>继续</td>
    </tr>
    <tr>
        <td>default</td>
        <td>默认</td>
    </tr>
    <tr>
        <td>do</td>
        <td>运行</td>
    </tr>
    <tr>
        <td>else</td>
        <td>否则</td>
    </tr>
    <tr>
        <td>for</td>
        <td>循环</td>
    </tr>
    <tr>
        <td>if</td>
        <td>如果</td>
    </tr>
    <tr>
        <td>instanceof</td>
        <td>实例</td>
    </tr>
    <tr>
        <td>return</td>
        <td>返回</td>
    </tr>
    <tr>
        <td>switch</td>
        <td>根据值选择执行</td>
    </tr>
    <tr>
        <td>while</td>
        <td>循环</td>
    </tr>
    <tr>
        <td rowspan="6">错误处理</td> 
        <td>assert</td>
        <td>断言表达式是否为真</td>
    </tr>
    <tr>
        <td>catch</td>
        <td>捕捉异常</td>
    </tr>
    <tr>
        <td>finally</td>
        <td>有没有异常都执行</td>
    </tr>
    <tr>
        <td>throw</td>
        <td>抛出一个异常对象</td>
    </tr>
    <tr>
        <td>throws</td>
        <td>声明一个异常可能被抛出</td>
    </tr>
    <tr>
        <td>try</td>
        <td>捕获异常</td>
    </tr>
    <tr>
        <td rowspan="2">包相关</td>
        <td>import</td>
        <td>引入</td>
    </tr>
    <tr>
        <td>package</td>
        <td>包</td>
    </tr>
    <tr>
        <td rowspan="8">基本类型</td>
        <td>boolean</td>
        <td>布尔型</td>
    </tr>
    <tr>
        <td>byte</td>
        <td>字节型</td>
    </tr>
    <tr>
        <td>char</td>
        <td>字符型</td>
    </tr>
    <tr>
        <td>double</td>
        <td>双精度浮点</td>
    </tr>
    <tr>
        <td>float</td>
        <td>单精度浮点</td>
    </tr>
    <tr>
        <td>int</td>
        <td>整型</td>
    </tr>
    <tr>
        <td>long</td>
        <td>长整型</td>
    </tr>
    <tr>
        <td>short</td>
        <td>短整型</td>
    </tr>
    <tr>
        <td rowspan="3">变量引用</td>
        <td>super</td>
        <td>父类，超类</td>
    </tr>
    <tr>
        <td>this</td>
        <td>本类</td>
    </tr>
    <tr>
        <td>void</td>
        <td>无返回值</td>
    </tr>
    <tr>
        <td rowspan="2">保留关键字</td>
        <td>goto</td>
        <td>是关键字但是不能使用</td>
    </tr>
    <tr>
        <td>const</td>
        <td>是关键字，但不能使用</td>
    </tr>
</table>

__注意__：Java 的 null 不是关键字，类似于 true 和 false，它是一个字面常量，不允许作为标识符使用  

## Java注释
+ 用于注释说明解释程序的文件称之为注释  
    （什么关于作者啦～对于程序的解释啦～～～都可以写为注释）
+ Java中的注释类型
  + 单行注释
  + 多行注释
  + 文档注释(Java特有)
+ 注释可以提高代码的阅读型，是你调试程序的重要方法
+ 写注释是一个好习惯，必须要养成
+ 可以用注释的方法，整理自己的思想，再用代码去实现
+ 特点：单行注释和多行注释，注释了的内容不参与编译。换句话说，编译后的class文件不包含注释掉的信息
+ 文档注释的使用：
  + 注释内容可以被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现的该程序的说明文档 

```java
/**
@author kogasa_touhou
@version v1.0
*/
public class HelloWorld {
   /* 这是第一个Java程序
    * 它将输出 Hello World
    * 这是一个多行注释的示例
    */
    public static void main(String[] args){
       // 这是单行注释的示例
       /* 这个也是单行注释的示例 */
       System.out.println("Hello World"); 
    }
}
```

## Java空行
空白行或者有注释的行，Java 编译器都会忽略掉

## 继承（inheritance）
### 继承性的好处
  + 减少了代码的冗余，提高了代码的复用性
  + 便于功能的扩展
  + 为之后的多态性，提供了前提
### 继承性的格式：class A extends B{}
```java
class fulei {

    }
class zilei extends fulei {

}
```
  + A:子类、派生类、subclass
  + B:父类、基类、superclass
  + 体现： 
    + 一旦子类A继承父类B以后，子类A就获取了父类B中声明的所有属性和方法
    + 特别的：父类中声明为private的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构
    + 只有因为封装性的影响，使得子类不能直接调用父类的结构而已
    + 子类继承父类以后，还可以声明自己特有的属性或方法，实现功能的扩展
    + 子类和父类的关系，不同于子集和集合的关系
+ 需要注意的是 Java 不支持多继承，但支持多重继承
![20211218154229-2021-12-18-15-42-29](http://kogasaimgbed.oss-cn-beijing.aliyuncs.com/noteimgs/20211218154229-2021-12-18-15-42-29.png)
>继承关键字  

继承可以使用 extends 和 implements 这两个关键字来实现继承，而且所有的类都是继承于 java.lang.Object，当一个类没有继承的两个关键字，则默认继承object（这个类在 java.lang 包中，所以不需要 import）祖先类  

#### extends 关键字
```java
public class Animal { 
    private String name;   
    private int id; 
    public Animal(String myName, String myid) { 
        //初始化属性值
    } 
    public void eat() {  //吃东西方法的具体实现  } 
    public void sleep() { //睡觉方法的具体实现  } 
} 
 
public class Penguin  extends  Animal{ 
}
```
#### implements关键字

使用 implements 关键字可以变相的使java具有多继承的特性，使用范围为类继承接口的情况，可以同时继承多个接口（接口跟接口之间采用逗号分隔）

```java
public interface A {
    public void eat();
    public void sleep();
}
 
public interface B {
    public void show();
}
 
public class C implements A,B {
}
```

#### super与this 关键字  

__super__ 关键字:  
    super表示使用它的类的父类。可用于：   

+ 调用父类的构造方法
+ 调用父类的方法（子类覆盖了父类的方法时）
+ 访问父类的数据域（可以这样用。但是没有必要）
+ 调用方法：  
  
```java
super();
super(参数列表);
```
+ 注意：super 语句必须是子类构造方法的第一条语句。不能在子类中使用父类构造方法名来调用父类构造方法。 父类的构造方法不被子类继承。调用父类的构造方法的唯一途径是使用 super 关键字，如果子类中没显式调用，则编译器自动将 super(); 作为子类构造方法的第一条语句。这会形成一个构造方法链。

静态方法中不能使用 super 关键字。

调用父类的方法语法：
```java 
super.方法名(参数列表);
```
如果是继承的方法，是没有必要使用 super 来调用，直接即可调用。但如果子类覆盖或重写了父类的方法，则只有使用 super 才能在子类中调用父类中的被重写的方法。  

__this__ 关键字：

指向自己的引用

this 关键字表示当前对象。可用于：

+ 调用当前类的构造方法，并且必须是方法的第一条语句。如：this(); 调用默认构造方法。this(参数); 调用带参构造方法  
+ 限定当前对象的数据域变量。一般用于方法内的局部变量与对象的数据域变量同名的情况。如 this.num = num。this.num 表示当前对象的数据域变量 num，而 num 表示方法中的局部变量

#### final关键字  
final关键字声明类可以把类定义为不能继承的，即最终类;  
或者用于修饰方法，该方法不能被子类重写  
+ 声明类：
```java
final class 类名 {//类体}
```
+ 声明方法： 
```java
修饰符(public/private/default/protected) final 返回值类型 方法名(){//方法体}
```

__注__:实例变量也可以被定义为 final，被定义为 final 的变量不能被修改。被声明为 final 类的方法自动地声明为 final，但是实例变量并不是 final
