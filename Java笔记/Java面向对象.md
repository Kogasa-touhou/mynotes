- [Java面向对象](#java面向对象)
  - [Java继承](#java继承)
    - [继承的概念](#继承的概念)
    - [继承关键字](#继承关键字)
    - [构造器](#构造器)
    - [Java 转型问题](#java-转型问题)
  - [Java 重写(Override)与重载(Overload)](#java-重写override与重载overload)
    - [重写(Override)](#重写override)
    - [重载(Overload)](#重载overload)
    - [重写与重载之间的区别](#重写与重载之间的区别)
  - [Java多态](#java多态)
    - [多态的优点](#多态的优点)
    - [多态存在的三个必要条件](#多态存在的三个必要条件)
    - [实现方式](#实现方式)
  - [Java抽象类和抽象方法](#java抽象类和抽象方法)
    - [abstract 关键字的使用](#abstract-关键字的使用)
    - [抽象类的匿名子类](#抽象类的匿名子类)
  - [接口](#接口)
    - [接口与类的相似点](#接口与类的相似点)
    - [接口与类的区别](#接口与类的区别)
    - [接口特性](#接口特性)
    - [抽象类和接口的区别](#抽象类和接口的区别)
    - [接口的声明、实现和继承](#接口的声明实现和继承)
    - [标记接口](#标记接口)
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



## Java多态  
多态是同一个行为具有多个不同表现形式或形态的能力  
多态就是同一个接口，使用不同的实例而执行不同操作  

### 多态的优点  
+ 消除类型之间的耦合关系
+ 可替换性
+ 可扩充性
+ 接口性
+ 灵活性
+ 简化性

### 多态存在的三个必要条件  
+ 继承  
+ 重写  
+ 父类引用指向子类对象 
    Parent p = new Child(); 

### 实现方式 
+ [重写](#java-重写override与重载overload) 
+ [接口](#接口)
+ [抽象类和抽象方法](#java抽象类和抽象方法)

## Java抽象类和抽象方法  
由于继承性的存在，一个个新的子类被定义。父类更加趋向于一般，更加通用。有时候我们将一个父类设计得非常抽象，以至于没有具体得实例，这样的类叫做抽象类  

### abstract 关键字的使用  

+ abstract: 抽象的
+ abstract可以用来修饰的结构:类、方法
+ abstract修饰类，这就是抽象类
  + 此类不能实例化
  + 抽象类中一定有构造器，便于子类实例化时调用
  + 开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作
+ abstract修饰方法:抽象方法  
  + 抽象方法只有方法的声明，没有方法体
  + 包含抽象方法的类，一定是抽象类。反之，抽象类中不一定有抽象方法
  + 若子类重写了父类中的所有抽象方法，则可以进行实例化。
  + 若子类没有重写父类中所有的抽象方法，则子类也是抽象方法，需要使用abstract修饰
+ abstract使用上的注意点
  + 不能用来修饰属性、构造器等结构
  + 不能用来修饰私有方法、静态方法、final的方法和类

```java
public class AbstractTest {
    public static void main(String[] args) {


        //一旦Person类抽象了，就不可实例化
        Person p1 = new Person();
        p1.eat();
    }
}

abstract class Person {
    String name;
    int age;

    //这不是抽象方法
    //public Person() {

    //}

    //抽象方法
    public abstract void eat();

    public Person(String name,int age) {
        this.name = name;
        this.age = age;
    }

    public void eat() {
        System.out.println("人干饭");
    }

    public void walk() {
        System.out.println("人跑路");
    }


}


class Students extends Person {

    public Student(String name,int age) {
        super(name.age);
    }

    public void eat() {

    }
}
```

### 抽象类的匿名子类

+ 匿名对象
``` java
method(new Student());
```
+ 非匿名类的非匿名对象  
```java
Worker worker = new Woker();
method1(Worker);
```
+ 非匿名类的匿名对象
```java
method1(new Worker());
```
+ 创建匿名子类的匿名对象
```java
method1(new Person(){
    @override
    //....
});
```

## 接口

Java类是不支持多继承的，使用接口就可以实现多重继承的效果  
它是一个抽象类型，和类是平行关系  
类可以描述对象的属性和方法，接口则包含类要实现的方法  

### 接口与类的相似点  
+ 一个接口可以有多种方法 
+ 接口文件保存在 .java 结尾的文件中，文件名使用接口名  
+ 接口的字节码文件保存在 .class 结尾的文件中  
+ 接口相应的字节码文件必须在与包名称相匹配的目录结构中  

### 接口与类的区别  
+ 接口不能用于实例化对象  
+ 接口没有构造方法  
+ 接口中所有的方法必须是抽象方法，Java 8 之后 接口中可以使用 default 关键字修饰的非抽象方法  
+ 接口不能包含成员变量，除了 static 和 final 变量  
+ 接口不是被类继承了，而是要被类实现  
+ 接口支持多继承  

### 接口特性  
+ 接口中每一个方法也是隐式抽象的,接口中的方法会被隐式的指定为 public abstract（只能是 public abstract，其他修饰符都会报错）
+ 接口中可以含有变量，但是接口中的变量会被隐式的指定为 public static final 变量（并且只能是 public，用 private 修饰会报编译错误） 
+ 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法  

### 抽象类和接口的区别  
+ 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行  
+ 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 public static final 类型的  
+ 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法  
+  一个类只能继承一个抽象类，而一个类却可以实现多个接口  
+  JDK 1.8 以后，接口里可以有静态方法和方法体了 
+  JDK 1.8 以后，接口允许包含具体实现的方法，该方法称为"默认方法"，默认方法使用 default 关键字修饰。 
+  JDK 1.9 以后，允许将方法定义为 private，使得某些复用的代码不会把方法暴露出去。  

### 接口的声明、实现和继承
> 声明 
```java

[可见度] interface 接口名称 [extends 其他的接口名] {
        // 声明变量
        // 抽象方法
}
```
> 实现  

类使用implements关键字实现接口  
Implements关键字放在class声明后面  
```java
...implements 接口名称[, 其他接口名称, 其他接口名称..., ...] ...
```
规则: 
+ 类在实现接口的方法时，不能抛出强制性异常，只能在接口中，或者继承接口的抽象类中抛出该强制性异常  
+ 类在重写方法时要保持一致的方法名，并且应该保持相同或者相兼容的返回值类型  
+ 如果实现接口的类是抽象类，那么就没必要实现该接口的方法  
+ 一个类可以同时实现多个接口
+ 一个类只能继承一个类，但是能实现多个接口  
+ 一个接口能继承另一个接口，这和类之间的继承比较相似  

> 继承 

和类之间继承类似，使用extends关键字进行继承  

```java
public interface Sports{
   public void setHomeTeam(String name);
   public void setVisitingTeam(String name);
}
public interface Football extends Sports{
   public void homeTeamScored(int points);
   public void visitingTeamScored(int points);
   public void endOfQuarter(int quarter);
}
public interface Hockey extends Sports{
   public void homeGoalScored();
   public void visitingGoalScored();
   public void endOfPeriod(int period);
   public void overtimePeriod(int ot);
}
```
多重继承:  
```java 
public interface Hockey extends Sports, Event
```  
### 标记接口  

标记接口是没有任何方法和属性的接口.它仅仅表明它的类属于一个特定的类型,供其他代码来测试允许做一些事情  

