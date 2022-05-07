[Toc]
# Java面向对象

## Java继承

### 继承的概念  

继承就是从已有的类派生出新的类，使得子类对象（实例）具有父类的实例域和方法，或者子类继承父类的方法，使得子类拥有和父类一样的行为。  

> 类的继承格式

``` java
class 父类 {

}
class 子类 extends 父类 {

}
```

如果类 B 从类 A 派生，或者说类 B 扩展自类 A，或者说类 B 继承类 A，
则称类 A 为"父类"，也称为超类、基类；
称类 B 为"子类"，也称为次类、扩展类、派生类。

子类从它的父类中继承可访问的数据域和方法，也可以添加新的数据域和新的方法。

关于继承的注意点:
+ 子类不是父类的子集，子类一般比父类包含更多的数据域和方法。
+ 父类中的 private 数据域在子类中是不可见的，因此在子类中不能直接使用它们。
+ 继承是为"是一个"的关系建模的，父类和其子类间必须存在"是一个"的关系，否则不能用继承。
+ Java 只允许单一继承（即一个子类只能有一个直接父类），C++ 可以多继承（即一个子类有多个直接父类）


> 为什么需要继承

重复的代码容易造成程序的臃肿.

在不同的类中也可能会有共同的特征和动作，可以把这些共同的特征和动作放在一个类中，让其它类共享。

因此可以定义一个通用类，然后将其扩展为其它多个特定类，这些特定类继承通用类中的特征和动作。

> 继承类型

需要注意的是 Java 不支持多继承，但支持多重继承。

![](https://kogasaimgbed.oss-cn-beijing.aliyuncs.com/noteimgs/20220506131328.png)

### 继承关键字

继承可以通过extends和implements这两个关键字来实现继承，所有的类都是继承于java.lang.Object。所以object类是所有类的父类。由于这个类在java.lang包中，所以并不需要**import** 。

> **extends** 关键字

由于单继承性，所以一个子类只能拥有一个父类，所以**extends**只能继承一个类。

```java
public class Animal {
    private String name;
    private int id;
    public Animal(String myNamem,int myid){
        //初始化
    }

    public void eat(){
        system.out.println("吃东西的具体实现")；
    }
    public void sleep(){
        system.out.println("睡觉的具体实现")；
    }
}

public class Pig extends Animal{

}
```
> **implements** 关键字

使用接口可以变相使得java具有多继承的特性，使用范围为类继承接口的情况，可以同时继承多个接口（接口之间使用逗号隔开）。

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

> **super** 与 **this** 

>> super关键字  

用来实现对父类成员的访问，用来引用当前对象的父类。主要用于：

+ 调用父类的构造方法；
+ 调用父类的方法（子类覆盖了父类的方法时）；
+ 访问父类的数据域（可以这样用但没有必要这样用）

调用父类构造方法语法：

```java
super();
或者
super(参数列表);
```

调用父类的方法语法: 

```java
super.方法名(参数列表);
````

注意：

+ super 语句必须是子类构造方法的第一条语句。
+ 不能在子类中使用父类构造方法名来调用父类构造方法。 
+ 父类的构造方法不被子类继承。
+ 调用父类的构造方法的唯一途径是使用 super 关键字，如果子类中没显式调用，则编译器自动将 super(); 作为子类构造方法的第一条语句。
+ 静态方法中不能使用 super 关键字。
+ 如果是继承的方法，是没有必要使用 super 来调用，直接即可调用。
+ 如果子类覆盖或重写了父类的方法，则只有使用 super 才能在子类中调用父类中的被重写的方法。


>> this关键字

指向自己的引用,表示当前对象，可用于:

+ 调用当前类的构造方法，并且必须是方法的第一条语句。如：this(); 调用默认构造方法。this(参数); 调用带参构造方法。

+ 限定当前对象的数据域变量。一般用于方法内的局部变量与对象的数据域变量同名的情况。如 this.num = num。this.num 表示当前对象的数据域变量 num，而 num 表示方法中的局部变量。

> **final** 关键字

final可以用来修饰变量（包括属性、对象属性、局部变量和形参）、方法（包括类方法和对象方法）和类。意为"最终的"

有几点需要注意一下: 
 + final 修饰类中的属性或者变量
    对于基本类型来说，是变量存放的值不能改变 
    对于引用数据类型来说，是指代地址不能改变并不是地址所指的对象或数组内容不可变  
    final 修饰属性，声明变量时可以不赋值，而且一旦赋值就不能被修改了。  
    对 final 属性可以在三个地方赋值：声明时、初始化块中、构造方法中，总之一定要赋值。  

+ final修饰类中的方法
    作用：可以被继承，但继承后不能被重写。
+ final修饰类
    作用：类不可以被继承。

>> 声明类

```java
final class 类名 {
    //类体
}
```

>> 声明方法 

```java
修饰符(public/private/default/protected) final 返回值类型 方法名(){
    //方法体
}

```

PS：final中的类，其属性、方法不是final的

### 构造器

子类不会继承父类的构造器，只会采用调用的模式（隐式或者显式）。

如果父类的构造器带参，则必须在子类的构造器中显式地通过super关键字调用父类得构造器并配以适当的参数列表

如果父类的构造器没有参数，则系统会自动调用，不需要使用super关键字

```java
class SuperClass {
    private int n;
    SuperClass() {
        System.out.println("SuperClass()");
    }
    superClass(int n) {
        System.out.println("SuperClass(int n)");
        this.n = n;
    }
}
// SubClass 类继承
class SubClass extends SuperClass {
    private int n;

    SubClass() {
        //自动调用父类的无参的构造器
        System.out.println("SubClass");
    }
    public SubClass(int n) {
        super(300);//调用父类中带有参数的构造器
        System.out.println("SubClass(int n) : " + n);
        this.n = n;
    }
}
// SubClass2 类继承
class SubClass2 extends SuperClass{
    private int n;
  
    SubClass2(){
        super(300);  // 调用父类中带有参数的构造器
        System.out.println("SubClass2");
  }  
  
    public SubClass2(int n){ // 自动调用父类的无参数构造器
        System.out.println("SubClass2(int n):"+n);
        this.n = n;
    }
}
public class TestSuperSub{
    public static void main (String args[]) {
        System.out.println("------SubClass 类继承------");
        SubClass sc1 = new SubClass();
        SubClass sc2 = new SubClass(100); 
        System.out.println("------SubClass2 类继承------");
        SubClass2 sc3 = new SubClass2();
        SubClass2 sc4 = new SubClass2(200); 
    }
}

```

输出结果为：

```bash
------SubClass 类继承------
SuperClass()
SubClass
SuperClass(int n)
SubClass(int n):100
------SubClass2 类继承------
SuperClass(int n)
SubClass2
SuperClass()
SubClass2(int n):200
```

### Java 转型问题

分为: 向上转型 (upcasting) 、向下转型(downcasting)  

例子: 
```java
Father f1 = new Son();// upcasting
//现在f1引用指向一个Son对象

Son s1 = (Son)f1; //downcasting
//现在f1 还是指向Son对象

Father f2 = new Father();
Son s2 = (Son)f2; //报错，子类引用不能指向父类对象
```

总结: 
+ 父类引用指向子类对象，而子类引用不能指向父类对象。
+ 父类申明变量指向子类实例，该父类变量不能调用父类不存在的变量和方法，否则会编译错误
+ 把子类对象直接赋给父类引用叫upcasting向上转型，向上转型不用强制转换
+ 把指向子类对象的父类引用赋给子类引用叫向下转型(downcasting)，要强制转换，如： 
f1 就是一个指向子类对象的父类引用。把f1赋给子类引用 s1 即 Son s1 = (Son)f1;
其中 f1 前面的(Son)必须加上，进行强制转换。 

## Java 重写(Override)与重载(Overload)

### 重写(Override)

重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。  
重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。  
重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。  

> 方法重写的规则  
+ 参数列表与被重写方法的参数列表必须完全相同。  
+ 返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类  
+ 访问权限不能比父类中被重写的方法的访问权限更低。  
+ 父类的成员方法只能被它的子类重写。  
+ 声明为 final 的方法不能被重写。  
+ 声明为 static 的方法不能被重写，但是能够被再次声明。 
+ 子类和父类在同一个包中，那么子类可以重写父类所有方法，除了声明为 private 和 final 的方法。  
+ 子类和父类不在同一个包中，那么子类只能够重写父类的声明为 public 和 protected 的非 final 方法。  
+ 重写的方法能够抛出任何非强制异常，无论被重写的方法是否抛出异常。但是，重写的方法不能抛出新的强制性异常，或者比被重写方法声明的更广泛的强制性异常，反之则可以。  
+ 构造方法不能被重写。  
+ 如果不能继承一个类，则不能重写该类的方法。  
+ 当需要在子类中调用父类的被重写方法时，要使用 super 关键字。  

### 重载(Overload)
重载(overloading) 是在一个类里面，方法名字相同，而参数不同。  
返回类型可以相同也可以不同。  
同样的一个方法能够根据输入数据的不同，做出不同的处理  
每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。  
最常用的地方就是构造器的重载。  

> 重载规则  
+ 被重载的方法必须改变参数列表(参数个数或类型不一样)；  
+ 被重载的方法可以改变返回类型；  
+ 被重载的方法可以改变访问修饰符；  
+ 被重载的方法可以声明新的或更广的检查异常；  
+ 方法能够在同一个类中或者在一个子类中被重载。  
+ 无法以返回值类型作为重载函数的区分标准。  

### 重写与重载之间的区别  

<table>
    <tr>
        <td>区别点</td>
        <td>重载方法</td>
        <td>重写方法</td>
    </tr>
    <tr>
        <td>参数列表</td>
        <td>必须修改</td>
        <td>一定不能修改</td>
    </tr>
    <tr>
        <td>返回类型</td>
        <td>可以修改</td>
        <td>一定不能修改</td>
    </tr>
    <tr>
        <td>异常</td>
        <td>可以修改</td>
        <td>可以减少或删除，一定不能抛出新的或者更广的异常</td>
    </tr>
    <tr>
        <td>访问</td>
        <td>可以修改</td>
        <td>一定不能做更严格的限制（可以降低限制）</td>
    </tr>
</table>





