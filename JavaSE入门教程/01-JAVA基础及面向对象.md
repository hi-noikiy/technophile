---
title: 01 - JavaSE之基础及面向对象

date: 2017-12-10 21:57:05
categories:
- JAVA

tags:
- JAVA
- 面向对象

---

# JAVA基础知识

- Java 是SUN（Stanford University Network，斯坦福大学网络公司）1995年推出的一门面向 Internet 的高级编程语言。

- Java 虚拟机（JVM:Java Virtual Machine）

- JRE（Java Runtime Environment）:Java 运行环境
  *（包括 JVM 和 Java 程序所需的核心类库等，给用户使用的）*
  JDK（Java Development Kit）Java开发工具包（包括JRE，给Java开发人员使用的）


- 使用 set 设置临时环境变量

  ```java
  set Path=xxx
  ```


- 在写简单的 HelloWorld 程序的时候，可以使得 java 文件名与类名不一致，最后得到的字节码文件的文件名是和类名相同的；**当包含 main 函数的类有 public 的时候，必须使得java文件名和类名一致，规定的**。


- 注意区别 set classpath=c:\  与  set classpath=c:\;  的区别**（分号的有无）**，不加分号只在当前目录找，加了分号先到当前目录找。所以以后不要加分号为好。


- 注意 path 和 classpath 查找先后的区别：
  **path是先到当前目录查找，没找到，再到path环境查找；**
  **classpath 是先到 classpath 环境查找，没找到，再到当前目录查找（前提加了分号）**


- 文档说明书：对于文档注释，是java特有的注释，其中注释内容可以被JDK提供的工具 javadoc.exe 所解析，生成一套以网页文件形式体现的该程序的说明文档


---


## 配置 JAVA 开发环境

```java
JAVA_HOME = D:\jdk1.8.0_144
PATH = .;%PATH%;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
CLASSPATH = .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
```



## JAVA 环境安装验证

```
java -version
javac -version
```




## 第一个 JAVA 程序

```java
public class Demo
{
    public static void main(String[] args)
    {
        System.out.println("Hello Java!");
    }
}
```

---


# 标识符

- 标识符的组成：**数字，字母，下划线，美元符号**

- 开头不能使用数字。

- 可以使用中文作为变量名（编辑代码的文本要为GBK格式，才能支持中文作为变量名）




# JAVA中的名称规范

- 包名：多单词组成时所有字母都小写**（xxxyyyzzz）**

- 类名接口名：多单词组成时，所有的单词的首字母大写**（XxxYyyZzz）**

- 变量名和函数名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写**（xxxYyyZzz）**

- 常量名：所有字母都大写，多单词时每个单词用下划线连接**（XXX_YYY_ZZZ）**


---


# 常量与变量

## 常量

- JAVA中可以通过 **final** 关键字定义常量。例如：final int i = 0;


## 数据类型


- 数据类型 = 基本数据类型 + 引用数据类型

- 基本数据类型 = 整数型（byte,short,int,long） + 浮点型（float,double） + 字符型（char） + 布尔型（boolean）

- 引用数据类型 = 类（class） + 接口（interface） + 数组（[]）


**1、整数型**

byte(-128 ~ 127)
short(-32768 ~ 32767)
int(-2147483648 ~ 2147483647)

Tips:
- **JAVA 中没有无符号整数型变量**
- 隐式类型转换（byte,short,char->int->long->float->double）
- byte,short,char之间不会相互转换，它们三者之间在计算时首先转换成int类型，然后进行计算。
- 容量大的数据类型转换成容量小的数据类型时，要加强制转换符，但是会造成精度降低或者溢出。
- **有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那一种，然后再进行计算。**

**2、浮点型**

- JAVA 中 float 型浮点数加上后缀 f 或 F。
- JAVA 中 double 型浮点数加上后缀 d 或 D。
- JAVA 浮点数的默认类型是 double。
- 将一个 float 类型的数，强制转换成 long 类型，会舍去小数部分，而不是四舍五入。


**3、逻辑型和字符型**
- JAVA中的逻辑型又叫布尔型，是一种只能表示 true 和 false 两种值的类型。
- JAVA中的字符型占用**两个字节**，能够表示 Unicode 字符（比如汉字）。

```java
char c1 = 'c';
char c2 = '冯';
```

**4、引用数据类型**

- JAVA 中的引用数据类型类似 C 语言中的指针类型；
- JAVA 中的引用数据类型主要用于类 class 定义的复杂数据类型（不是基本的数据类型，在代码里面是不会高亮显示的，**如String类型，是class定义的复杂数据类型。**）
- JAVA 中引用数据类型变量和常量的定义方式与基本数据类型相同。
- 引用数据类型包括：类class，接口interface，数组。




---



# 运算符

**1、算术运算符**

- ++和-- 优先级最高
- 乘,/,% 优先级其次
- +和- 优先级最低
- 括号可以改变优先级

> Tips:
> 1、如果对负数取模，可以把模数的负号忽略，如 5%-2=1，但是被模数是负数就另当别论。
> 2、对于除号"/"，它的整数除和小数除是由区别的：整数之间做除法时，只保留整数部分而舍弃小数部分；小数之间做除法时（不论除数是小数还是被除数是小数）结果都是浮点类型。
> 3、"+"号除了字符串相加功能之外，还能把非字符串转化为字符串。(System.out.println("5+5="+5+5); **"+"运算符两侧的操作数只要有一个是字符串String类型，系统会自动将另一个操作数转换成字符串然后在进行连接。**)



**2、逻辑运算符**

- ! 运算优先级最高
- && 运算优先级其次
- || 运算优先级最低
- 括号可以改变优先级


**3、关系运算符**

- JAVA 中同类型的变量和常量都可以使用 == 和 != 来判断是否相等；
- JAVA 中关系运算符的结果是个布尔值，而不是C语言中的1或0；
- 关系运算符常和逻辑运算符一起使用。

**4、位运算符**

- 位运算符是对整数进行二进制操作的运算符，返回的结果也是一个整数；
- 位运算符有按位取反~，按位与&，按位或|和按位异或^；
- 移位运算符是左移<<，右移>>，**无符号右移>>>**.


**5、条件运算符**

- Java中的条件运算符根据条件来返回一个值
- x = (布尔表达式) ? (为true时所赋的值) : (为false时所赋的值);
- 例如：String s = (num < 2500)?("房贷没压力"):("房贷太高了");




---



**1、if-else-**
- 略

**2、switch-case-**
- switch语句中的条件表达式只能是**int,short,byte,char**
- switch语句中的case后必须是**常量**且不能重复。


---




# 成员变量

成员变量（类的属性）和局部变量的区别：

- 成员变量：**如果没有初始化和赋值的话，默认初始值为 0**

- 局部变量：没有初始化的时候，**访问**的时候会报错


---



# 引用
- JAVA 语言中除了基本类型之外的变量类型都称之为引用类型，如String类型。

> 当使用String s; 的时候，实际上有两片内存，一片是一个索引叫s（栈），里面装的是一个地址；当 s = new String("JAVA"); 的时候，s才指向另一片空间（堆），这篇空间的内容为 "JAVA"。所以s并不是"JAVA"，而是"JAVA"的引用。

> **一提到引用的概念，立马想到一小块内存（栈）指向一大块内存（堆）。**



---



# 构造方法
- 使用new + 构造方法 创建一个新对象
- 当没有指定构造函数时，编译器为类自动添加默认构造函数。
- 构造方法是在 JAVA 类中的一个用来初始化对象的函数
- 构造方法与类同名且没有返回值


---

> **第三章内存解析6-11课实在是太精彩了，不多说，自己看！！！**



---


# 方法重载(Overload)
- 方法名相同 + 参数不同：参数个数不同/参数类型不同
- 返回值类型不同（不构成重载）

与普通方法一样，构造方法也可以重载



--------

# 不同类型的内存分布
- **当创建该类对象的时候，静态变量、静态方法就会被放到内存里了，就算没有new一个对象，static静态变量依然存在于 data segment 区域。**

- 内存分为四个区：**stack segment，heap segment，data segment，code segment；**
  **stack** 区存放函数参数和局部变量；
  **heap**  区存放对象（包括成员变量：成员变量在堆内存分配，因为成员变量只有在new出来的时候才会分配空间，所以分配在堆内存；而局部变量分配在栈内存。）；
  **data**  区存放static 的变量或者字符串常量； 
  **code**  区存放类中的方法；




---



# this 指针

- 在类的方法定义中使用的this关键字代表使用该方法的对象的引用。
- **哪个对象调用该方法的this，this就指向哪个对象。**
- this可以看成一个成员变量，它的值是当前对象的引用。


---


# static关键字

- 在类中，用static声明的成员变量为静态成员变量，它为该类的功用变量，在第一次使用（第一次new一个对象的时候）的时候被初始化，对于该类的所有对象来说，static成员变量只有一份。
- **用static声明的方法为静态方法，在调用该方法的时候，不会将对象的引用传递给它，所以在static方法中不可以方位非static的成员。**
- static成员变量分配在数据区，所以内存的布局，除了 stack 和 heap 之外又多了一块 Data Segment 区域。
- 静态成员变量可以使用 “类名.静态成员变量” 来访问，当然也可以使用 “对象.静态成员变量” 来访问。


- **静态成员函数不能调用非静态成员成员变量和非静态成员函数，因为静态的成员函数不需要new一个对象出来（使用static声明的方法为静态方法，在调用该方法的时候，不会将对象的引用传递给它，所以在static方法中不可访问非static成员），既然没有对象，那么其内的非静态成员变量和非静态成员函数就无法执行，所以静态成员函数不能调用非静态成员成员变量和非静态成员函数。**

- 静态与非静态的成员变量都可以在定义的时候赋值，只不过意义不同。


---


# package 和 import

-  为了便于管理大型软件系统中数目众多的类，解决类的命名冲突的问题，java引入包（package）机制，提供类的多重类命名空间。相当于对相同名字的不同类加上了一个独一无二的路径。

-  package 语句作为 java 源文件的第一条语句，指明该文件中定义的类所在的包。（若缺省包语句，则为无名包）

-  给包取名，约定俗成的是公司的域名倒过来：例如公司为www.google.com，那么给你的类打包时取名可以是：package com.google.javatest;等。

-  java编译器把包对应于文件系统的目录管理，package语句中，用"."来指明包目录的层次，如上package com.google.javatest，表示该文件中所在的类位于 "./com/google/javatest"目录下。**如果其他的类调用了该文件中的类，那么该文件的类对应的class文件就需要位于"./com/google/javatest" 目录下。**

-  假如该文件中的一个类叫Cat类，那么在其他类使用的时候，比如new一个Cat对象，那么就要这么写： 

  ```java
  com.google.javatest.Cat cat = new com.google.javatest.Cat();
  ```

  **需要把Cat类的路径加上，否则找不到这个Cat类（如果将一个类打包，则使用该类时，必须使用该类的全名，java编译器才能找到该类）。这样就太麻烦了，解决办法就是使用import。使用import在文件的开头引入要使用的类，例如 import com.google.javatest.Cat;import com.google.javatest.*;**

-  **可以不需要使用 import 语句直接使用java.lang包中的类，比如String类**。

-  注意打包的源文件可能对编译产生影响，可以将打完包（生成了对应的class文件）的源文件（java源文件）删除或者转移目录。

-  **注意：如果按照以上import com.google.javatest.Cat;的写法，那么我们调用Cat类的 java 源文件的路径要和com路径位于同一层目录，否则又会找不到路径。（必须class文件的最上层的包的父目录位于classpath下。比如上面的class文件最上层的包是com目录，com目录的父目录是当前目录，就是"."目录，是位于classpath目录下的。）**


---


# java提供的包

> 怎么看java提供的包有哪些呢？位于D:\Java\jdk\jre\lib\rt.jar里面，解压出就可以看到。

主要包介绍：

- java.lang 包含一些java语言的核心类，如String，Math，Integer，System和Thread，提供常用功能。
- java.awt  包含了构成抽象窗口工具集的多个类，这些类被用来构建和管理应用程序的图形用户界面（GUI）。
- java.applet 包含applet运行所需的一些类。
- java.net 包含执行与网络相关的操作的类。
- java.io 包含能提供多种输入输出功能的类。
- Java.util 包含一些实用工具类，如sing一系统特性，实用与日期日历相关的函数。

PS:可以不需要使用import语句直接使用java.lang包。

> 怎么打包我们自己的包为jar文件呢？执行：jar -cvf xxx.jar path（path表示你需要打包的包的路径）

可以把jar包文件当成路径设置到classpath变量，这样我们就可以使用jar包。效果和真实的路径相同。

---



# 继承和权限控制

| 修饰符       | 类内部  | 同一个包 | 子类(可以不同的包) | 不同包的非子类 |
| --------- | ---- | ---- | ---------- | ------- |
| private   | yes  |      |            |         |
| default   | yes  | yes  |            |         |
| protected | yes  | yes  | yes        |         |
| public    | yes  | yes  | yes        | yes     |


- **类的可见性**

1. **java 语言规定一个文件只能有一个类被声明为 public**
2. **public的类必须与文件名完全相同。**
3. public类可以被其他包中的类导入使用，default类只能被同一个包内部的类访问
4. **protected 和 private 不能用于限定类的可见性，对类的修饰权限只能使用public和default**


- **类的继承**

1. java中使用 extends 关键字实现类的继承机制。
2. java只支持单继承，不允许多继承。


- **一些建议**

1. 每个属性和方法都显式声明访问权限，不使用默认权限。
2. 对于逻辑上对外不可见的属性和方法尽量设置为private。
3. 虽然java语言中同一个包中的其他非子类可以自由访问protected成员，但这是不推荐的。
4. 将逻辑上相关的类组织在一个包中，以包的形式组织程序的类。


---



# 方法重写（override/overwrite）

- 在子类中可以根据需要对从基类中继承来的方法进行重写。

- 重写方法必须与被重写方法具有相同的方法名称，参数列表，返回值。（就是方法一模一样才行）

- 重写方法不能使用比被重写方法更严格的访问权限。




---

# super关键字

- 在java中使用 super 来引用基类的成员。

- 当子类和父类有同名成员变量的时候，子类成员变量不会覆盖父类成员变量，子类成员变量重写父类的成员变量，使得父类成员变量被隐藏，使用super 可以访问父类成员变量。

**-当一个子类继承父类时，相当于子类自动多了两个成员变量，一个是this，指向子类对象，一个是super指向子类对象中的父类对象。**




# 继承中的构造方法

- 子类的构造过程中必须调用其基类的构造方法**（先父母，后客人，最后自己）**

- **子类可以在自己的构造方法中使用 super 调用基类的构造方法（使用 this调用本类的另外构造方法）**

- **如果子类的构造方法没有显式调用基类的构造方法，则系统默认调用基类的无参数的构造方法。**

- **如果子类构造方法中既没有显式调用基类构造方法，而基类中又没有无参数的构造方法，则编译出错。**


---



# Object 类之 toString 方法

- Object类是所有 java 类的根基类。

- 如果在类的声明中未使用 extends 关键字指明其基类，则默认基类为Object 类。

- Object 类的 toString 方法，建议所有子类覆盖此方法（It is recommended that all subclasses override this method.）





# Object类之 equals 方法

- Object 类中定义 public boolean equals(Object obj) 方法，提供对象是否相等的逻辑。

- Object 的 equals 方法定义为：x.equals(y)当x和y是同一个对象的引用时返回 true，否则返回 false。

- java SDK 提供的一些类，如String，Date等，重写了Object的 equals 方法，调用这些类的 equals 方法，x.equals(y)当x 和y 所引用的对象是同一类对象且属性相同时（并不一定是相同对象），返回 true，否则返回false。

- 可以根据需要重写equals方法。


---


# 对象转型

- 一个基类的引用类型变量可以指向其子类的对象。

- 一个基类的引用不可以访问其子类对象新增加的成员（属性和方法）。

- 可以使用（引用变量 instanceof 类名）来判断该引用型变量所指向的对象是否属于**该类或该类的子类**。

- 子类的对象可以当做基类的对象来使用称作向上转型，反之成为向下转型。


---



# 多态/动态绑定/迟绑定

- 动态绑定是指在执行期间（而非编译期间）判断所引用对象的实际类型，根据其实际的类型调用其相应的方法。

- 条件：

1. **要有继承**
2. **子类重写父类方法**
3. **父类引用指向子类对象**

- **当父类引用指向子类对象的时候，父类对象不能访问子类新增的成员变量和成员方法。**


---


# 抽象类

- 用 **abstract** 关键字来修饰一个类时，这个类叫做抽象类；用 abstract 来修饰一个方法时，该方法叫做抽象方法。

- **含有抽象方法的类必须被声明为抽象类，抽象类必须被继承，抽象方法必须被重写。**

- **抽象类不能被实例化。**

- **抽象方法只需声明，而不需要实现。**


---


# final 关键字

- **final 的变量（成员变量，局部变量）的值不能被改变。**

- **final 的方法不能被重写。**

- **final 的类不能被继承。**


---

# interface 接口

- 接口是抽象方法和常量值的定义的集合。

- 从本质上讲，接口是一种特殊的抽象类，这种抽象类只包含常量（static final类型的成员变量）和方法的定义，而没有变量和方法的实现。

- 接口实现方式：

```java
interface Singer {
    public void sing();
    public void sleep();
}

class Student implements Singer { // 学生不是继承（extends）Singer，而是实现（implements）Singer
    
}
```

- 多个无关的类可以实现（implements 类似继承）同一个接口。

```java

interface Singer {
    public void sing();
    public void sleep();
}

class Student implements Singer {
	// ...
}

class Dog implements Singer {
    // ...
}

```

- 一个类可以实现（implements 类似继承）多个无关的接口。

```java
class Teacher implements Singer, Painter {
}
```

- 与继承关系类似，接口与实现类之间存在多态性。




## 接口特性

- 接口可以多重实现。

- **接口中的成员变量默认为 public static final 的；也只能是 public static final 的。**

- **接口中只能定义抽象方法，而且这些成员方法默认为public的，也只能是public的。**

- 接口可以继承其他的接口，并添加新的属性和抽象方法。



> 如果两个接口有相同的方法，但是有个类同时实现了这两个接口会怎样呢？

* 只需要实现一次就好了。*

> 如果两个接口有名称相同的方法，只是返回值不一样，但是有个类同时实现了这两个接口会怎样呢？

* 你说同时实现这两个方法就好了，但是这两个方法并不构成重载，无法区分这两个方法的，所以目前无解，记住不要这样实现。哈哈，以后查到了再说。*


- 子类重写父类的方法时，方法的访问权限必须等于或大于父类的方法访问权限，也就是说实现接口的方法的权限必须为public，因为接口的方法为public。
  否则编译的错误为：
```java
* Test.java:44: 错误: Worker中的playWithPet()无法实现PetCarer中的playWithPet()
        void playWithPet() {
             ^
  正在尝试分配更低的访问权限; 以前为public *
```


