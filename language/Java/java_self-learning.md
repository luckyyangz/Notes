# Java Self-learning

> 参考资料：《Thinking in Java (Fourth ed)》

[TOC]

## 1. Java基础简介

### Java特性

面向对象
分布式
解释型
高性能（与其他解释型的脚本语言相比）
多线程
动态的

### Java 三大体系

+ JavaSE (J2SE) (Java2 Platform Standard Edition，java平台标准版)
+ JavaEE (J2EE) (Java 2 Platform,Enterprise Edition，java平台企业版)
+ JavaME(J2ME)(Java 2 Platform Micro Edition，java平台微型版)

2005年6月，JavaOne大会召开，SUN公司公开Java SE 6。此时，Java的各种版本已经更名以取消其中的数字"2"：J2EE更名为Java EE, J2SE更名为Java SE，J2ME更名为Java ME

### 开发前需了解

JDK (Java Development Kit) ：编写Java程序的程序员使用的软件
JRE (Java Runtime Environment)：运行Java程序的用户使用的软件
Server JRE (Java SE Runtime Environment)：服务端使用的 Java 运行环境
SDK (Software Development Kit)：软件开发工具包，在Java中用于描述1998年~2006年之间的JDK
DAO (Data Access Object)：数据访问接口，数据访问，顾名思义就是与数据库打交道
MVC (Model View Controller)：模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用于组织代码用一种业务逻辑和数据显示分离的方法

### 类

### 接口






---

## 2. 环境安装配置

### 配置环境变量说明

+ JAVA_HOME:

> 一是为了方便引用，比如，JDK安装在C:\jdk1.6.0目录里，则设置JAVA_HOME为该目录路径, 那么以后要使用这个路径的时候, 只需输入%JAVA_HOME%即可, 避免每次引用都输入很长的路径串;
> 
> 二则是归一原则, 当JDK路径改变的时候, 仅需更改JAVA_HOME的变量值即可, 否则,就要更改任何用绝对路径引用JDK目录的文档, 要是万一没有改全, 某个程序找不到JDK, 后果是可想而知的----系统崩溃!
> 
> 三则是第三方软件会引用约定好的 JAVA_HOME 变量, 不然, 你不能正常使用该软件。
> 
> 在系统环境变量那一栏中点 -> 新建 JAVA_HOME （JAVA_HOME指向的是JDK的安装路径）

+ PATH 变量

> path 变量使得我们能够在系统中的任何地方运行java应用程序，比如 javac、java、javah 等等,这就要找到我们安装 JDK 的目录，
> 
> 假设我们的JDK安装在 C:\jdk1.6.0 目录下,那么在 C:\jdk1.6.0\bin 目录下就是我们常用的 java 应用程序,我们就需要把 C:\jdk1.6.0\bin 这个目录加到 path 环境变量里面。

+ CLASS_PATH 变量

> classpath 环境变量，是当我们在开发java程序时需要引用别人写好的类时，要让 java 解释器知道到哪里去找这个类。通常，sun 为我们提供了一些额外的丰富的类包，一个是 dt.jar，一个是 tools.jar，这两个 jar 包都位于 C:\jdk1.6.0\lib 目录下，所以通常我们都会把这两个 jar 包加到我们的 classpath 环境变量中 set classpath=.;C:\jdk1.6.0\lib\tools.jar;C:\jdk1.6.0\lib\dt.jar。

注意在完成配置环境变量后测试JDK是否安装成功时键入命令：java -version

### 配置步骤

+ 配置环境

https://www.jianshu.com/p/acb1f062a925
https://segmentfault.com/q/1010000002719737
https://www.jianshu.com/p/e4e8bb5e391f?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation

2018-01-25 删除了`~/.bash_profile`这个文件，以下是对该文件的记录：

```shell
# This is my personal bash_profile, when loaded at login.

# User specific environment and startup programs

# =========2017.02.04==========
# virtualenvwrapper
# export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python
# export WORKON_HOME=~/virtualenvs
# [ -f /usr/local/bin/virtualenvwrapper.sh  ] && source /usr/local/bin/virtualenvwrapper.sh
# [ -f /etc/bash_completion.d/virtualenvwrapper  ] && source /etc/bash_completion.d/virtualenvwrapper# export PIP_VIRTUALENV_BASE=$WORKON_HOME
# export PIP_RESPECT_VIRTUALENV=true

# =========2017.01.17==========

# GOROOT
export GOROOT=/usr/local/go
# GOPATH
export GOPATH=$HOME/gotest
# GOROOT bin
export PATH=$PATH:$GOROOT/bin
# GOPATH bin
# export PATH=$PATH:$GOPATH/bin

# =========2018-01-25==========

export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_161.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
export CLASS_PATH=$JAVA_HOME/lib

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi
```


+ 安装java及环境配置

安装完最新的JAVA、JDK、JRE，查看JDK真实路径

```shell
~ » /usr/libexec/java_home -v
java_home: option requires an argument -- v
/Library/Java/JavaVirtualMachines/jdk1.8.0_161.jdk/Contents/Home
```

配置`~/.bash_profile`文件，将下述信息复制在其后
其中，`JAVA_HOME`后粘贴的是JDK的真实路径

```shell
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_161.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
export CLASS_PATH=$JAVA_HOME/lib
```

配置完后保存退出，使用`source ~/.bash_profile`，可以使用`echo $PATH`来检查是否生效

+ 安装tomcat

（暂不需要）
tomcat其实是一个用java语言开发的免费开源的web服务器
可参考：https://www.atatech.org/articles/97768

+ 安装Maven

[Maven介绍](https://www.zhihu.com/question/20104186)
[mac下配置java环境，tomcat以及IntelliJ的配置](https://www.jianshu.com/p/e4e8bb5e391f?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)


### 配置IntelliJ IDEA







---







## 3. Java编程

### Chp1 & Chp2 对象入门&一切都是对象

#### 引用

用引用操作对象

创建一个`String`引用，并不是对象。

```java
String s;   /*引用s并没有和任何事物相关联*/
/* 安全的做法：创建引用同时也初始化
 * 这里用到Java一个特性：字符串可以用带引号的文本初始化 */
String s = "asdf";  
```

#### 对象

**一般的做法创建对象**

```java
String s = new String("asdf");
```

**对象存储的位置**

1) 寄存器(Registers)
2) 堆栈(Stack)。位于通用RAM中，通过堆栈指针可以直接从CPU获得直接支持。Java对象引用存储于此，但对象并不存储于其中。
3) 堆(Heap)。一种通用的内存池，也位于RAM区。用于存放所有的Java对象。**堆不同于堆栈的好处是：编译器不需知道存储的数据在堆里存活多长时间。**因此在堆里分配存储有很大的灵活性。当需要一个对象时，`new`一行代码，会自动在堆里进行分配。但相应的代价是，用堆进行存储分配和清理需要更长时间。
4) 常量存储(Constant storage)。直接存放在代码内部。
5) 非RAM存储。数据完全存活于程序之外。两类：流对象、持久化对象。Java提供了对轻量级持久化的支持，而JDBC和Hibernate这样的机制提供更加复杂的对在数据库中存储/读取信息的支持。

**特例：基本类型**

对于特别小、简单的变量，Java采取和C/C++相同的方法，不用`new`创建变量，而是创建一个并非是引用的“自动”变量，直接存储值，并置于堆栈中，因此更加高效。基本类型所占存储大小的固定性，也是Java比其他语言编写程序更具可移植性的原因之一。
![-w500](media/15168749811820/15171345472674.jpg)

+ 所有数值类型都有正负号
+ 基本类型具有的包装器类，使得可以在堆中创建一个非基本对象，用来表示对应的基本类型。自动包装功能，能将基本类型转换为包装器类型
+ 高精度数字：两个类：`BigInteger`、`BigDecimal`，虽然他们大体都属于包装器类的范畴，但二者都没有对应的基本类型。

**数组**

Java保证数组会被初始化，且不能再它范围之外被访问（C/C++无法保证）。
创建数组实际是创建了一个引用数组，每个引用会被自动初始化为特定值：`null`，如果试图使用还是`null`的引用，运行时将会报错。常犯的数组错误就可以避免。

**永远不需要销毁对象**

作用域(scope)

以下代码在c、c++中是合法的，但是在Java中却不能这样书写，认为导致程序的混乱。

```java
{
    int x = 12;
    {
        int x = 96;     // Illegal
    }
}
```

以下代码，引用`s`在作用域终点就消失了，`s`指向的`String`对象仍占据内存空间。事实证明，用`new`创建的对象，只要需要都会一直保留下去。而C++则需要考虑在使用完后将其销毁的问题。Java的**垃圾回收器**，来负责这一处理，解决了内存泄漏的问题。

#### 创建新的数据类型：类

在Java中所有工作就是定义类、产生类的对象、以及发送消息给这些对象。
定义了一个类，在类中设置两种类型的元素：

+ 字段 (Fields)：可以是任何类型的对象，可以通过其引用与其通信；也可以是基本类型中的一种
+ 方法 (Methods)

普通field不能在对象间共享。

引用一个对象的成员，给字段赋值：`objRef.member = 47;`等类似。

基本类型如果没有进行初始化，也会赋有初始值。

```java
// 示例创建类和对象
class DataOnly {
    int i;
    double d;
    boolean b;
}

DataOnly data = new DataOnly();
```

#### 方法、参数和返回值

```java
int storage(String s) {
    return s.length() * 2;
}
```

```java
boolean flag() { return true; }
float naturalLogBase() { return 2.718; }
void nothing() { return; }  //返回空
void nothing2() {}  // 返回空
```

#### 构建Java程序

**名字的可见性** 

_反转域名_ 确保所有文件都自动存在于自己的命名空间中。

```java
com.bruceeckel.utility.foibles;
```

**使用其他组件**

```java
import java.util.Vector;
import java.util.*; // util包含了数量众多的类，希望使用若干，但不用全部声明它们
```

**static 关键字**

一旦将什么东西设为static，数据或方法就不会同那个类的任何对象实例联系到一起。所以尽管从未创建那个类的一个对象，仍能调用一个 _static方法_ ，或访问一些 _static数据_ 。
对于非static数据和方法，我们必须创建一个对象，并用那个对象访问数据或方法。
这是由于非static数据和方法必须知道它们操作的具体对象。

对方法来说，**static一项重要的用途**就是帮助我们在不必创建对象的前提下调用那个方法。正如以后会看到的那样，这一点是至关重要的——特别是在定义程序运行入口方法main()的时候。

```java
class StaticTest {
    static int i = 47;  // 为了将数据成员(或方法)设为static，只需在定义前置和这个关键字即可
}

/** 
 * 尽管我们制作了两个StaticTest对象，但它们仍然只占据StaticTest.i的一个存储空间
 * 都共享同样的i
 */
StaticTest st1 = new StaticTest();
StaticTest st2 = new StaticTest();

// 有两个办法可引用一个static变量：
st2.i   // 1. 通过对象引用
StaticTest.i++; // 2. 通过类名引用
```

类似的逻辑也适用于**静态方法**：

```java
class StaticFun {
    static void incr() { StaticTest.i++; }  // 静态方法
}

// 通过对象调用
StaticFun sf = new StaticFun();
sf.incr();

// 通过类直接调用
StaticFun.incr();
```

#### 第一个Java程序

```java
// Property.java    类名与文件是一样的
import java.util.*;

public class Property {
  /**
   * 1. 类里必须包含一个名为main()的方法
   * 2. 关键字"public"意味着方法可由外部世界调用
   * 3. main()的自变量是包含了String对象的一个数组。
   *    args不会在本程序中用到，但需要在这个地方列出，
   *    因为它们保存了在命令行调用的自变量。
   */ 
  public static void main(String[] args) {
    System.out.println(new Date());
    Properties p = System.getProperties();
    p.list(System.out);
    System.out.println("--- Memory Usage:");
    Runtime rt = Runtime.getRuntime();
    System.out.println("Total Memory = "
                       + rt.totalMemory()
                       + " Free Memory = "
                       + rt.freeMemory());
  }
}
```

#### 注释和嵌入文档

注意javadoc只能为public（公共）和protected（受保护）成员处理注释文档。
“private”（私有）和“友好”（详见5章）成员的注释会被忽略，我们看不到任何输出（也可以用-private标记包括private成员）。
因为只有public和protected成员才可在文件之外使用，这是客户程序员的希望。然而，所有类注释都会包含到输出结果里。
具体格式查看：https://java.quanke.name/2.8%20注释和嵌入文档.html 




### Chp3: 控制程序流程

#### 使用Java运算符

**方法调用中的别名处理**

```java
//: PassObject.java
// Passing objects to methods can be a bit tricky

class Letter {
  char c;
}

public class PassObject {
  static void f(Letter y) {
    y.c = 'z';
  }
  public static void main(String[] args) {
    Letter x = new Letter();
    x.c = 'a';
    System.out.println("1: x.c: " + x.c);
    f(x);
    System.out.println("2: x.c: " + x.c);
  }
} ///:~
```

输出结果如下:

```java
1: x.c: a
2: x.c: z
```

**算数运算符**

创建随机数：

```java
//: MathOps.java
// Demonstrates the mathematical operators
import java.util.*;

public class MathOps {
  // Create a shorthand to save typing:
  static void prt(String s) {
    System.out.println(s);
  }
  // shorthand to print a string and an int:
  static void pInt(String s, int i) {
    prt(s + " = " + i);
  }
  // shorthand to print a string and a float:
  static void pFlt(String s, float f) {
    prt(s + " = " + f);
  }
  public static void main(String[] args) {
    // Create a random number generator,
    // seeds with current time by default:
    Random rand = new Random();
    int i, j, k;
    // '%' limits maximum value to 99:
    j = rand.nextInt() % 100;
    k = rand.nextInt() % 100;
    pInt("j",j);  pInt("k",k);
    i = j + k; pInt("j + k", i);
    i = j - k; pInt("j - k", i);
    i = k / j; pInt("k / j", i);
    i = k * j; pInt("k * j", i);
    i = k % j; pInt("k % j", i);
    j %= k; pInt("j %= k", j);
    // Floating-point number tests:
    float u,v,w;  // applies to doubles, too
    v = rand.nextFloat();
    w = rand.nextFloat();
    pFlt("v", v); pFlt("w", w);
    u = v + w; pFlt("v + w", u);
    u = v - w; pFlt("v - w", u);
    u = v * w; pFlt("v * w", u);
    u = v / w; pFlt("v / w", u);
    // the following also works for
    // char, byte, short, int, long,
    // and double:
    u += v; pFlt("u += v", u);
    u -= v; pFlt("u -= v", u);
    u *= v; pFlt("u *= v", u);
    u /= v; pFlt("u /= v", u);
  }
} ///:~
```

**关系运算符**

检查对象是否相等

```java
//: Equivalence.java

public class Equivalence {
  public static void main(String[] args) {
    Integer n1 = new Integer(47);
    Integer n2 = new Integer(47);
    System.out.println(n1 == n2);   // 不相等，句柄不同
    System.out.println(n1 != n2);   // 不相等，句柄不同
  }
} ///:~
```

```java
//: EqualsMethod.java

public class EqualsMethod {
  public static void main(String[] args) {
    Integer n1 = new Integer(47);
    Integer n2 = new Integer(47);
    System.out.println(n1.equals(n2));  // 相等，对比两个对象实际内容是否相同
    // 但这个方法不适用于“主类型”，那些类型直接使用==和!=即可。
  }
} ///:~



//: EqualsMethod2.java

class Value {
  int i;
}

public class EqualsMethod2 {
  public static void main(String[] args) {
    Value v1 = new Value();
    Value v2 = new Value();
    v1.i = v2.i = 100;
    System.out.println(v1.equals(v2));
    // 又变成不相等了，因为equals默认比较句柄。除非在自己的新类中改变了equals()
    // 大多数Java类库都实现了equals()，所以它实际比较的是对象的内容，而非它们的句柄。
  }
} ///:~
```

**逻辑运算符**

只可将AND，OR或NOT应用于布尔值（与C++不同）

对浮点数字的比较是非常严格的。即使一个数字仅在小数部分与另一个数字存在极微小的差异，仍然认为它们是“不相等”的。即使一个数字只比零大一点点（例如2不停地开平方根），它仍然属于“非零”值。

逻辑运算符的“短路”特性

**按位运算符**

暂时未看

**三元if-else运算符**

它确实属于运算符的一种，因为它最终也会生成一个值。这与本章后一节要讲述的普通if-else语句不同。
若打算频繁用它，负面效果是，代码可读性差。

```java
布尔表达式 ? 值0:值1
```

**逗号运算符**

Java里需要用到逗号的唯一场所就是for循环。

**字串运算符**

在Java里有一项特殊用途：连接不同的字串。
若表达式以一个String起头，那么后续所有运算对象都必须是字串。如下所示：

```java
// 表达式以一个String起头，后续所有运算对象都必须是字串
int x = 0, y = 1, z = 2;
String sString = "x, y, z ";
System.out.println(sString + x + y + z);

// 然而，如果使用下述语句：早期版本的Java就会提示出错（以后的版本能将x转换成一个字串）
System.out.println(x + sString);

// 请务必保证第一个元素是字串（或加上引号的一系列字符，编译能将其识别成一个字串）
```

**造型运算符**

在适当的时候，Java会将一种数据类型自动转换成另一种。例如，假设我们为浮点变量分配一个整数值，计算机会将int自动转换成float。

进行一次cast，要将括号中希望的数据类型（包括所有修改符）置于其他任何值的左侧。下面是一个例子，但在这儿展示的两种情况下，cast是多余的，编译器会自动完成：

```java
void casts() {
    int i = 200;
    long l = (long)i;   // 多余
    long l2 = (long)200;    // 多余
}
```

Java允许我们将任何主类型“造型”为其他任何一种主类型，但布尔值（bollean）要除外，后者根本不允许进行任何造型处理。

**Java没有“sizeof”**

Java不需要sizeof()运算符来满足这方面的需要，因为所有数据类型 _在所有机器的大小都是相同的_ 。我们不必考虑移植问题——Java本身就是一种“与平台无关”的语言。

#### 执行控制

Java使用了C的全部控制语句。在Java里，涉及的关键字包括if-else、while、do-while、for以及一个名为switch的选择语句。





### Chp4: 初始化和清除

> C++为我们引入了“构建器”的概念。这是一种特殊的方法，在一个对象创建之后自动调用。Java也沿用了这个概念，但新增了自己的“垃圾收集器”，能在资源不再需要的时候自动释放它们。

#### 用构建器自动初始化

构建器属于一种较特殊的方法类型，因为它没有返回值。这与void返回值存在着明显的区别。对于void返回值，尽管方法本身不会自动返回什么，但仍然可以让它返回另一些东西

```java
//: SimpleConstructor.java
// Demonstration of a simple constructor
package c04;

class Rock {
  Rock(int i) { // This is the constructor
    // 构建器的名字必须与类名完全相同
    System.out.println(
      "Creating Rock number " + i);
  }
}

public class SimpleConstructor {
  public static void main(String[] args) {
    for(int i = 0; i < 10; i++)
      new Rock(i);
  }
} ///:~
```

#### 方法过载

为了让相同的方法名伴随不同的自变量类型使用，“方法过载”是非常关键的一项措施。同时，尽管方法过载是构建器必需的，但它亦可应用于其他任何方法，且用法非常方便。

```java
//: Overloading.java
// Demonstration of both constructor
// and ordinary method overloading.
import java.util.*;

class Tree {
  int height;
  Tree() {  // no-arg constructors
    prt("Planting a seedling");
    height = 0;
  }
  Tree(int i) {
    prt("Creating new Tree that is "
        + i + " feet tall");
    height = i;
  }
  void info() {
    prt("Tree is " + height
        + " feet tall");
  }
  void info(String s) {
    prt(s + ": Tree is "
        + height + " feet tall");
  }
  static void prt(String s) {
    System.out.println(s);
  }
}

public class Overloading {
  public static void main(String[] args) {
    for(int i = 0; i < 5; i++) {
      Tree t = new Tree(i);
      t.info();
      t.info("overloaded method");
    }
    // Overloaded constructor:
    new Tree();
  }
} ///:~
```

**区分过载方法**

每个过载的方法都必须采取独一无二的自变量类型列表。即使自变量的顺序也足够我们区分两个方法（尽管我们通常不愿意采用这种方法，因为它会产生难以维护的代码）。

不能根据返回值类型来区分过载的方法。

**默认构建器**

没有自变量，作用是创建一个“空对象”。若创建一个没有构建器的类，则编译程序会帮我们自动创建一个默认构建器。

**this关键字**

this关键字（注意只能在方法内部使用）可为已调用了其方法的那个对象生成相应的句柄。
但要注意，假若准备从自己某个类的另一个方法内部调用一个类方法，就不必使用this。只需简单地调用那个方法即可。

this关键字只能用于那些特殊的类——需明确使用当前对象的句柄。例如，假若您希望将句柄返回给当前对象，那么它经常在return语句中使用。

```java
//: Leaf.java
// Simple use of the "this" keyword

public class Leaf {
  private int i = 0;
  Leaf increment() {
    i++;
    return this;
  }
  void print() {
    System.out.println("i = " + i);
  }
  public static void main(String[] args) {
    Leaf x = new Leaf();
    x.increment().increment().increment().print();
  }
} ///:~
```

**在构建器里调用构建器**

若为一个类写了多个构建器，那么经常都需要在一个构建器里调用另一个构建器，以避免写重复的代码。可用this关键字做到这一点。

这个例子也向大家展示了this的另一项用途。由于自变量s的名字以及成员数据s的名字是相同的，所以会出现混淆。为解决这个问题，可用this.s来引用成员数据。

```java
//: Flower.java
// Calling constructors with "this"

public class Flower {
  private int petalCount = 0;
  private String s = new String("null");
  Flower(int petals) {
    petalCount = petals;
    System.out.println(
      "Constructor w/ int arg only, petalCount= "
      + petalCount);
  }
  Flower(String ss) {
    System.out.println(
      "Constructor w/ String arg only, s=" + ss);
    s = ss;
  }
  Flower(String s, int petals) {
    this(petals);
//!    this(s); // Can't call two! 不能调用两个不同的构建器
    this.s = s; // Another use of "this"
    System.out.println("String & int args");
  }
  Flower() {
    this("hi", 47);
    System.out.println(
      "default constructor (no args)");
  }
  void print() {
//!    this(11); // Not inside non-constructor!
    System.out.println(
      "petalCount = " + petalCount + " s = "+ s);
  }
  public static void main(String[] args) {
    Flower x = new Flower();
    x.print();
  }
} ///:~
```

> 理解了this关键字后，我们可更完整地理解static（静态）方法的含义。它意味着一个特定的方法没有this。
> 我们不可从一个static方法内部发出对非static方法的调用，尽管反过来说是可以的。
> 若将一个static方法置入一个类的内部，它就可以访问其他static方法以及static字段。
> 有些人抱怨static方法并不是“面向对象”的，因为它们具有全局函数的某些特点。若您发现自己使用了大量静态方法，就应重新思考自己的策略。然而，static的概念是非常实用的，许多时候都需要用到它。

#### 清除：收尾和垃圾收集

垃圾收集器只知道释放那些由new分配的内存，所以不知道如何释放对象的“特殊”内存。Java提供了一个名为finalize()的方法，可在类里定义它。
一旦垃圾收集器准备好释放对象占用的存储空间，它首先调用finalize()，而且只有在下一次垃圾收集过程中，才会真正回收对象的内存。

具体参见：[4.3 清除：收尾和垃圾收集](https://java.quanke.name/4.3%20%E6%B8%85%E9%99%A4%EF%BC%9A%E6%94%B6%E5%B0%BE%E5%92%8C%E5%9E%83%E5%9C%BE%E6%94%B6%E9%9B%86.html)

#### 成员初始化

**明确进行的静态初始化**

```java
class Spoon {
  static int i;
  static {  // static构建从句, 静态块
    i = 47;
  }
  // . . .
```

```java
//: ExplicitStatic.java
// Explicit static initialization
// with the "static" clause.

class Cup {
  Cup(int marker) {
    System.out.println("Cup(" + marker + ")");
  }
  void f(int marker) {
    System.out.println("f(" + marker + ")");
  }
}

class Cups {
  static Cup c1;
  static Cup c2;
  static {
    c1 = new Cup(1);
    c2 = new Cup(2);
  }
  Cups() {
    System.out.println("Cups()");
  }
}

public class ExplicitStatic {
  public static void main(String[] args) {
    System.out.println("Inside main()");
    Cups.c1.f(99);  // (1)
  }
  static Cups x = new Cups();  // (2)
  static Cups y = new Cups();  // (2) 
} ///:~
```

**非静态实例的初始化**

针对每个对象的非静态变量的初始化，Java 1.1提供了一种 _类似的_ 语法格式。

#### 数组初始化

Java则没有象C++那样的“集合”概念，因为Java中的所有东西都是对象。但它确实有自己的数组，通过**数组初始化**来提供支持。

```java
int[] al;   // 定义数组，建议采用
int al[];   // 同上
```

编译器不允许我们告诉它一个数组有多大。这样便使我们回到了“句柄”的问题上。为了给数组创建相应的存储空间，必须编写一个初始化表达式。

对于数组，初始化工作可在代码的任何地方出现，但也可以使用一种特殊的初始化表达式，它必须在数组创建的地方出现。

```java
int[] a1 = { 1, 2, 3, 4, 5 };   // 特殊初始化
```

```java
//: ArrayNew.java
// Creating arrays with new.
package com.company.quickstart;

import java.util.*;


public class ArrayNew {
    static Random rand = new Random();
    private static int pRand(int mod) {
        return Math.abs(rand.nextInt()) % mod + 1;
    }
    public static void main(String[] args) {
        int[] a;
        a = new int[pRand(20)];     // 数组大小随机决定，不超过20
        // 若操作的是一个非基本类型对象的数组，那么无论如何都要使用new。
        // 因此，数组的创建实际是在运行期间进行的。
        prt("length of a = " + a.length);
        for(int i = 0; i < a.length; i++) {
            a[i] = i + 1;   // 如果不加此句，基本数据类型的数组元素会自动初始化成“空”值
            prt("a[" + i + "] = " + a[i]);
        }
    }
    private static void prt(String s) {
        System.out.println(s);
    }
} ///:~
```

数组初始化的第二种形式（Java 1.1开始支持）提供了一种更简便的语法:

```java
//: VarArgs.java
// Using the Java 1.1 array syntax to create
// variable argument lists

class A { int i; }

public class VarArgs {
  static void f(Object[] x) {
    for(int i = 0; i < x.length; i++)
      System.out.println(x[i]);
  }
  public static void main(String[] args) {
    f(new Object[] { 
        new Integer(47), new VarArgs(), 
        new Float(3.14), new Double(11.11) });
    f(new Object[] {"one", "two", "three" });
    f(new Object[] {new A(), new A(), new A()});
  }
} ///:~
```

**多维数组**

```java
//: MultiDimArray.java
// Creating multidimensional arrays.
import java.util.*;

public class MultiDimArray {
  static Random rand = new Random();
  static int pRand(int mod) {
    return Math.abs(rand.nextInt()) % mod + 1;
  }
  public static void main(String[] args) {
    int[][] a1 = {
      { 1, 2, 3, },
      { 4, 5, 6, },
    };
    for(int i = 0; i < a1.length; i++)
      for(int j = 0; j < a1[i].length; j++)
        prt("a1[" + i + "][" + j +
            "] = " + a1[i][j]);
    // 3-D array with fixed length:
    int[][][] a2 = new int[2][2][4];
    for(int i = 0; i < a2.length; i++)
      for(int j = 0; j < a2[i].length; j++)
        for(int k = 0; k < a2[i][j].length;
            k++)
          prt("a2[" + i + "][" +
              j + "][" + k +
              "] = " + a2[i][j][k]);
    // 3-D array with varied-length vectors:
    int[][][] a3 = new int[pRand(7)][][];
    for(int i = 0; i < a3.length; i++) {
      a3[i] = new int[pRand(5)][];
      for(int j = 0; j < a3[i].length; j++)
        a3[i][j] = new int[pRand(5)];
    }
    for(int i = 0; i < a3.length; i++)
      for(int j = 0; j < a3[i].length; j++)
        for(int k = 0; k < a3[i][j].length;
            k++)
          prt("a3[" + i + "][" +
              j + "][" + k +
              "] = " + a3[i][j][k]);
    // Array of non-primitive objects:
    Integer[][] a4 = {
      { new Integer(1), new Integer(2)},
      { new Integer(3), new Integer(4)},
      { new Integer(5), new Integer(6)},
    };
    for(int i = 0; i < a4.length; i++)
      for(int j = 0; j < a4[i].length; j++)
        prt("a4[" + i + "][" + j +
            "] = " + a4[i][j]);
    Integer[][] a5;
    a5 = new Integer[3][];
    for(int i = 0; i < a5.length; i++) {
      a5[i] = new Integer[3];
      for(int j = 0; j < a5[i].length; j++)
        a5[i][j] = new Integer(i*j);
    }
    for(int i = 0; i < a5.length; i++)
      for(int j = 0; j < a5[i].length; j++)
        prt("a5[" + i + "][" + j +
            "] = " + a5[i][j]);
  }
  static void prt(String s) {
    System.out.println(s);
  }
} ///:~
```




### Chp5: 隐藏实例过程

> “进行面向对象的设计时，一项基本的考虑是：如何将发生变化的东西与保持不变的东西分隔开。”
Java推出了“访问指示符”的概念，允许库创建者声明哪些东西是客户程序员可以使用的，哪些是不可使用的。作为一名库设计者，应将所有东西都尽可能保持为“private”（私有），并只展示出那些想让客户程序员使用的方法。
仍存在这样一个问题：如何将组件绑定到单独一个统一的库单元里。这是通过Java的package（打包）关键字来实现的，而且访问指示符要受到类在相同的包还是在不同的包里的影响。

#### 包：库单元

迄今为止，本书的大多数例子都仅存在于单个文件中，而且设计成局部（本地）使用，没有同包名发生冲突（在这种情况下，类名置于“默认包”内）。这是一种有效的做法，而且考虑到问题的简化，本书剩下的部分也将尽可能地采用它。然而，若计划创建一个“对因特网友好”或者说“适合在因特网使用”的程序，必须考虑如何防止类名的重复。

为Java创建一个源码文件的时候，它通常叫作一个“编辑单元”（有时也叫作“翻译单元”）。每个编译单元都必须有一个以.java结尾的名字。
在编译单元的内部，可以有一个**公共（public）类，它必须拥有与文件相同的名字（包括大小写形式，但排除.java文件扩展名）**。
**每个编译单元内都只能有一个public类（同样地，否则编译器会报告出错）。**
那个编译单元剩下的类（如果有的话）可在那个包之外隐藏起来，因为它们非public，而且它们由用于主public类的“支撑”类组成。

编译一个`.java`文件时，我们会获得一个名字完全相同的输出文件。
但对于`.java`文件中的每个类，它们都有一个`.class`扩展名。
与用汇编写过程不同，**在Java中一个有效的程序就是一系列.class文件，它们可以封装和压缩到一个JAR文件里**（使用Java 1.1提供的jar工具）。Java解释器负责对这些文件的寻找、装载和解释。

“库”也由一系列**类文件**构成。每个文件都有一个public类，所以每个文件都有一个**组件**。如果想将所有这些组件（它们在各自独立的.java和.class文件里）都归纳到一起，那么`package`关键字就可以发挥作用）。

若在一个文件的开头使用下述代码：`package mypackage;`，该语句必须作为文件的第一个非注释语句出现，指出这个编译单元属于mypackage库的一部分。如果其他人想使用这个名字， _要么指出完整的名字，要么与mypackage联合使用import关键字_ 。**注意根据Java包（封装）的约定，名字内的所有字母都应小写。**

**冲突**

若通过`*`导入了两个库，而且它们包括相同的名字，这时会出现什么情况呢？例如，假定一个程序使用了下述导入语句：

```java
import com.bruceeckel.util.*;
import java.util.*;
```

现在试着生成一个Vector，编译器会报告一个错误。假设我想使用标准的Java Vector，那么必须象下面这样编程：

```java
java.util.Vector v = new java.util.Vector();
```

**自定义工具库**

创建自己的工具库，以便减少或者完全消除重复的代码。可为`System.out.println()`创建一个别名，减少重复键入的代码量，它可以是名为tools的一个包（package）的一部分：

不同的数据类型现在都可以在一个新行输出（P.rintln()），或者不在一个新行输出（P.rint()）

```java
//: P.java
// The P.rint & P.rintln shorthand
package com.bruceeckel.tools;

public class P {
  public static void rint(Object obj) {
    System.out.print(obj);
  }
  public static void rint(String s) {
    System.out.print(s);
  }
  public static void rint(char[] s) {
    System.out.print(s);
  }
  public static void rintln() {
    System.out.println();
  }
  public static void rintln(Object obj) {
    System.out.println(obj);
  }
  public static void rintln(String s) {
    System.out.println(s);
  }
  public static void rintln(char[] s) {
    System.out.println(s);
  }
} ///:~
```

**条件编译**

一种很常见的用途就是调试代码。Alen Holub（www.holub.com）提出了利用包（package）来模仿条件编译的概念。

在第9章，大家还会学习一个更高级的错误控制工具，名为“违例控制”。

```java
//: Assert.java
// Assertion tool for debugging
package com.bruceeckel.tools.debug;

public class Assert {
  private static void perr(String msg) {
    System.err.println(msg);
  }
  public final static void is_true(boolean exp) {
    if(!exp) perr("Assertion failed");
  }
  public final static void is_false(boolean exp){
    if(exp) perr("Assertion failed");
  }
  public final static void 
  is_true(boolean exp, String msg) {
    if(!exp) perr("Assertion failed: " + msg);
  }
  public final static void 
  is_false(boolean exp, String msg) {
    if(exp) perr("Assertion failed: " + msg);
  }
} ///:~
```

如果想使用这个类，可在自己的程序中加入下面这一行：

```java
import com.bruceeckel.tools.debug.*;
```

如欲清除断定机制，以便自己能发行最终的代码，我们创建了第二个Assert类，但却是在一个不同的包里

```java
//: Assert.java
// Turning off the assertion output 
// so you can ship the program.
package com.bruceeckel.tools;

public class Assert {
  public final static void is_true(boolean exp){}
  public final static void is_false(boolean exp){}
  public final static void 
  is_true(boolean exp, String msg) {}
  public final static void 
  is_false(boolean exp, String msg) {}
} ///:~
```

假如将前一个import语句变成下面这个样子：

```java
import com.bruceeckel.tools.*;
```

程序便不再显示出断言。

#### Java访问指示符

针对类内每个成员的每个定义，Java访问指示符public，protected以及private都置于它们的最前面——无论它们是一个数据成员，还是一个方法。

**友好**

如果根本不指定访问指示符，通常称为“友好”（Friendly）访问，我们也说友好元素拥有“包访问”权限。

对于任何关系，一个非常重要的问题是“谁能访问我们的‘私有’或private代码”，方法：
> (1) 使成员成为“public”（公共的）。这样所有人从任何地方都可以访问它。
> (2) 变成一个“友好”成员，方法是舍弃所有访问指示符，并将其类置于相同的包内。这样一来，其他类就可以访问成员。
> (3) 正如以后引入“继承”概念后大家会知道的那样，一个继承的类既可以访问一个protected成员，也可以访问一个public成员（但不可访问private成员）。只有在两个类位于相同的包内时，它才可以访问友好成员。但现在不必关心这方面的问题。
> (4) 提供“访问器／变化器”方法（亦称为“获取／设置”方法），以便读取和修改值。这是OOP环境中最正规的一种方法，也是Java Beans的基础——具体情况会在第13章介绍。

**public：接口访问**

紧随在public后面的成员声明适用于所有人，特别是适用于使用库的客户程序员。

**private：不能接触**

除非那个特定的 _类_ ，而且从 _那个类的方法里_ ，否则没有人能访问那个成员。

同一个包内的其他成员不能访问private成员。另一方面，也不能由几个合作的人创建一个包。所以private允许我们自由地改变那个成员，同时毋需关心它是否会影响同一个包内的另一个类。

大家就会发现private仍然有非常重要的用途，特别是在涉及多线程处理的时候（详情见第14章）。

下例说明了使用private的方便：
> (1) 有时可能想控制对象的创建方式，并防止有人直接访问一个特定的构建器（或者所有构建器）。必须调用`makeASundae()`方法来实现。
> (2) 此时还会产生另一个影响：由于默认构建器是唯一获得定义的，而且它的属性是private，所以可防止对这个类的继承

```java
//: IceCream.java
// Demonstrates "private" keyword

class Sundae {
  private Sundae() {}
  static Sundae makeASundae() { 
    return new Sundae(); 
  }
}

public class IceCream {
  public static void main(String[] args) {
    //! Sundae x = new Sundae();    // 防止有人直接访问一个特定的构建器（或者所有构建器）
    Sundae x = Sundae.makeASundae();
  }
} ///:~
```

若确定一个类只有一个“助手”方法，那么对于任何方法来说，都可以把它们设为private，从而保证自己不会误在包内其他地方使用它，防止自己更改或删除方法。

**protected：“友好的一种”**

为我们引入了一种名为 _“继承”_ 的概念，它以现有的类为基础，并在其中加入新的成员，同时不会对现有的类产生影响——我们将这种现有的类称为“基础类”或者“基本类”（Base Class），亦可改变那个类现有成员的行为。对于从一个现有类的继承，我们说自己的新类“扩展”（extends）了那个现有的类。`class Foo extends Bar {`

+ 若新建一个包，并从另一个包内的某个类里继承，则唯一能够访问的成员就是原来那个包的public成员。
+ 如果在相同的包里进行继承，那么继承获得的包能够访问所有“友好”的成员。

_有些时候，基础类的创建者喜欢提供一个特殊的成员，并允许访问衍生类，这正是protected的工作。_

#### 接口与实现

通常认为访问控制是“隐藏实施细节”的一种方式，所以我们需要将接口同实施细节分离开。

可考虑用特殊的样式创建一个类：将public成员置于最开头，后面跟随protected、友好以及private成员。好处是类的使用者可从上向下依次阅读，首先看到对自己来说最重要的内容，并在遇到非公共成员后停止阅读，后者已经属于内部实施细节的一部分了。

#### 类访问

一些限制：

> (1) 每个编译单元（文件）都只能有一个public类。
> (2) public类的名字必须与包含了编译单元的那个文件的名字完全相符，甚至包括它的大小写形式。
> (3) 可能（但并常见）有一个编译单元根本没有任何公共类。此时，可按自己的意愿任意指定文件名。
> (4) 注意不可将类设成private（那样会使除类之外的其他东西都不能访问它），也不能设成protected。对于类的访问只有两个选择：“友好的”或者public。 _若不愿其他任何人访问那个类，可将所有构建器设为private。_ 这样一来，在类的一个static成员内部，除自己之外的其他所有人都无法创建属于那个类的一个对象。


```java
//: Lunch.java
// Demonstrates class access specifiers.
// Make a class effectively private
// with private constructors:

class Soup {
  private Soup() {}
  // (1) Allow creation via static method:
  public static Soup makeSoup() {
    return new Soup();
  }
  // (2) Create a static object and
  // return a reference upon request.
  // (The "Singleton" pattern):
  private static Soup ps1 = new Soup();
  public static Soup access() {
    return ps1;
  }
  public void f() {}
}

class Sandwich { // Uses Lunch
  void f() { new Lunch(); }
}

// Only one public class allowed per file:
public class Lunch {
  void test() {
    // Can't do this! Private constructor:
    //! Soup priv1 = new Soup();
    Soup priv2 = Soup.makeSoup();
    Sandwich f1 = new Sandwich();   // 注意！
    Soup.access().f();
  }
} ///:~
```

不想让别人为那个类创建对象，把它变成private， _但别人怎样使用这个类呢_ ？上面的例子为我们揭示出了两个选择。

第一个选择，我们可创建一个static方法，再通过它创建一个新的Soup，然后返回指向它的一个句柄。如果想在返回之前对Soup进行一些额外的操作，或者想了解准备创建多少个Soup对象（可能是为了限制它们的个数），这种方案无疑是特别有用的。

第二个选择是采用“设计模式”（Design Pattern）技术，本书后面会对此进行详细介绍。通常方案叫作“独子”，因为它仅允许创建一个对象。类Soup的对象被创建成Soup的一个static private成员，所以有一个而且只能有一个。除非通过public方法access()，否则根本无法访问它。





### Chp6: 类再生

> 第一个最简单：在新类里简单地创建原有类的对象。我们把这种方法叫作“合成”，因为新类由现有类的对象合并而成。我们只是简单地重复利用代码的功能，而不是采用它的形式。
> 第二个：继承（Inheritance）

#### 合成的语法

```java
//: SprinklerSystem.java
// Composition for code reuse
package c06;

class WaterSource {
  private String s;
  WaterSource() {
    System.out.println("WaterSource()");
    s = new String("Constructed");
  }
  public String toString() { return s; }    // 注意
}

public class SprinklerSystem {
  private String valve1, valve2, valve3, valve4;
  WaterSource source;
  int i;
  float f;
  void print() {
    System.out.println("valve1 = " + valve1);
    System.out.println("valve2 = " + valve2);
    System.out.println("valve3 = " + valve3);
    System.out.println("valve4 = " + valve4);
    System.out.println("i = " + i);
    System.out.println("f = " + f);
    System.out.println("source = " + source);   // 用到 toString()
  }
  public static void main(String[] args) {
    SprinklerSystem x = new SprinklerSystem();
    x.print();
  }
} ///:~
```

每种非基本类型的对象都有一个toString()方法。

如果不深究，可能会草率地认为编译器会为上述代码中的每个句柄都自动构造对象。但是打印语句的输出事实上是：

```java
valve1 = null
valve2 = null
valve3 = null
valve4 = null
i = 0
f = 0.0
source = null
```

如希望句柄得到初始化，可在下面这些地方进行：

> (1) 在对象定义的时候。这意味着它们在构建器调用之前肯定能得到初始化。
> (2) 在那个类的构建器中。
> (3) 紧靠在要求实际使用那个对象之前。这样做可减少不必要的开销——假如对象并不需要创建的话。

下面向大家展示了所有这三种方法：

```java
//: Bath.java
// Constructor initialization with composition

class Soap {
  private String s;
  Soap() {
    System.out.println("Soap()");
    s = new String("Constructed");
  }
  public String toString() { return s; }
}

public class Bath {
  private String 
    // Initializing at point of definition:
    s1 = new String("Happy"), 
    s2 = "Happy", 
    s3, s4;
  Soap castille;
  int i;
  float toy;
  Bath() {
    System.out.println("Inside Bath()");
    s3 = new String("Joy");
    i = 47;
    toy = 3.14f;
    castille = new Soap();
  }
  void print() {
    // Delayed initialization:
    if(s4 == null)
      s4 = new String("Joy");
    System.out.println("s1 = " + s1);
    System.out.println("s2 = " + s2);
    System.out.println("s3 = " + s3);
    System.out.println("s4 = " + s4);
    System.out.println("i = " + i);
    System.out.println("toy = " + toy);
    System.out.println("castille = " + castille);
  }
  public static void main(String[] args) {
    Bath b = new Bath();
    b.print();
  }
} ///:~
```

#### 继承的语法

```java
//: Detergent.java
// Inheritance syntax & properties

class Cleanser {
  private String s = new String("Cleanser");
  public void append(String a) { s += a; }
  public void dilute() { append(" dilute()"); }
  public void apply() { append(" apply()"); }
  public void scrub() { append(" scrub()"); }
  public void print() { System.out.println(s); }
  public static void main(String[] args) {
    Cleanser x = new Cleanser();
    x.dilute(); x.apply(); x.scrub();
    x.print();
  }
}

public class Detergent extends Cleanser {
  // Change a method:
  public void scrub() {
    append(" Detergent.scrub()");
    super.scrub(); // Call base-class version 
    /* super关键字，它引用当前类已从中继承的一个“超类”（Superclass）。
       所以表达式super.scrub()调用的是方法scrub()的基础类版本。*/
  }
  // Add methods to the interface:
  public void foam() { append(" foam()"); }
  // Test the new class:
  public static void main(String[] args) {
    Detergent x = new Detergent();
    x.dilute();
    x.apply();
    x.scrub();
    x.foam();
    x.print();
    System.out.println("Testing base class:");
    Cleanser.main(args);
  }
} ///:~
```

无论Cleanser还是Detergent都包含了一个main()方法。我们可为自己的每个类都创建一个main()。通常建议大家象这样进行编写代码，使自己的测试代码能够封装到类内。

在计划继承的时候，一个比较好的规则是 _将所有字段都设为private，并将所有方法都设为public_ （protected成员也允许衍生出来的类访问它；以后还会深入探讨这一问题）。当然，在一些特殊的场合，我们仍然必须作出一些调整，但这并不是一个好的做法。

可将继承想象成“对接口的重复利用”或者“接口的再生”。

+ 重复利用：scrub()
+ 接口再生：foam()

**初始化基础类**

下面这个例子向大家展示了对这种 _三级继承_ 的应用：

```java
//: Cartoon.java
// Constructor calls during inheritance

class Art {
  Art() {
    System.out.println("Art constructor");
  }
}

class Drawing extends Art {
  Drawing() {
    System.out.println("Drawing constructor");
  }
}

public class Cartoon extends Drawing {
  Cartoon() {
    System.out.println("Cartoon constructor");
  }
  public static void main(String[] args) {
    Cartoon x = new Cartoon();
  }
} ///:~
```

该程序的输出显示了自动调用：

```java
Art constructor
Drawing constructor
Cartoon constructor
```

_构建是在基础类的“外部”进行的，所以基础类会在衍生类访问它之前得到正确的初始化。_ 

用super关键字以及适当的自变量列表实现含有自变量的构建器:

```java
//: Chess.java
// Inheritance, constructors and arguments

class Game {
  Game(int i) {
    System.out.println("Game constructor");
  }
}

class BoardGame extends Game {
  BoardGame(int i) {
    super(i);
    System.out.println("BoardGame constructor");
  }
}

public class Chess extends BoardGame {
  Chess() {
    super(11);
    System.out.println("Chess constructor");
  }
  public static void main(String[] args) {
    Chess x = new Chess();
  }
} ///:~
```

#### 合成与继承的结合

许多时候都要求将合成与继承两种技术结合起来使用。

```java
//: PlaceSetting.java
// Combining composition & inheritance

class Plate {
  Plate(int i) {
    System.out.println("Plate constructor");
  }
}

class DinnerPlate extends Plate {
  DinnerPlate(int i) {
    super(i);
    System.out.println(
      "DinnerPlate constructor");
  }
}

class Utensil {
  Utensil(int i) {
    System.out.println("Utensil constructor");
  }
}

class Spoon extends Utensil {
  Spoon(int i) {
    super(i);
    System.out.println("Spoon constructor");
  }
}

class Fork extends Utensil {
  Fork(int i) {
    super(i);
    System.out.println("Fork constructor");
  }
}

class Knife extends Utensil {
  Knife(int i) {
    super(i);
    System.out.println("Knife constructor");
  }
}

// A cultural way of doing something:
class Custom {
  Custom(int i) {
    System.out.println("Custom constructor");
  }
}

public class PlaceSetting extends Custom {
  Spoon sp;
  Fork frk;
  Knife kn;
  DinnerPlate pl;
  PlaceSetting(int i) {
    super(i + 1);
    sp = new Spoon(i + 2);
    frk = new Fork(i + 3);
    kn = new Knife(i + 4);
    pl = new DinnerPlate(i + 5);
    System.out.println(
      "PlaceSetting constructor");
  }
  public static void main(String[] args) {
    PlaceSetting x = new PlaceSetting(9);
  }
} ///:~
```

**确保正确的清除**

垃圾收集器大多数时候都能很好地工作，但在某些情况下，我们的类可能在自己的存在时期采取一些行动，而这些行动要求必须进行明确的清除工作。

两个新关键字：try和finally。第9章才会向大家正式引荐它们。try关键字指出后面跟随的块（由花括号定界）是一个“警戒区”，它会受到特别的待遇。其中一种待遇就是：该警戒区后面跟随的finally从句的代码肯定会得以执行——不管try块到底存不存在。

在自己的清除方法中，必须注意对基础类以及成员对象清除方法的调用顺序——假若一个子对象要以另一个为基础。

#### 到底选择合成还是继承

> **如果想利用新类内部一个现有类的特性，而不想使用它的接口，通常应选择合成。也就是说，我们可嵌入一个对象，使自己能用它实现新类的特性。但新类的用户会看到我们已定义的接口，而不是来自嵌入对象的接口。考虑到这种效果，我们需在新类里嵌入现有类的private对象。**

> **有些时候，我们想让类用户直接访问新类的合成。也就是说，需要将成员对象的属性变为public。成员对象会将自身隐藏起来，所以这是一种安全的做法。见下例：**

> **“属于”关系是用继承来表达的，而“包含”关系是用合成来表达的。**

```java
//: Car.java
// Composition with public objects

class Engine {
  public void start() {}
  public void rev() {}
  public void stop() {}
}

class Wheel {
  public void inflate(int psi) {}
}

class Window {
  public void rollup() {}
  public void rolldown() {}
}

class Door {
  public Window window = new Window();
  public void open() {}
  public void close() {}
}

public class Car {
  public Engine engine = new Engine();
  public Wheel[] wheel = new Wheel[4];
  public Door left = new Door(),
       right = new Door(); // 2-door
  Car() {
    for(int i = 0; i < 4; i++)
      wheel[i] = new Wheel();
  }
  public static void main(String[] args) {
    Car car = new Car();
    car.left.window.rollup();
    car.wheel[0].inflate(72);
  }
} ///:~
```

#### protected

在继承的概念下，protected这个关键字有了意义。
在理想情况下，private成员随时都是“私有”的，任何人不得访问。但在实际应用中，经常想把某些东西深深地藏起来，但同时允许访问衍生类的成员。protected关键字可帮助我们做到这一点。
“它本身是私有的，但可由从这个类继承的任何东西或者同一个包内的其他任何东西访问”

#### 上溯造型

#### final关键字

详情见：[6.8 final关键字](https://java.quanke.name/6.8%20final%E5%85%B3%E9%94%AE%E5%AD%97.html)








### Chp7: 多形性 (多态性)

> 对于面向对象的程序设计语言， _多形性 (也称多态，Polymorphism)_ 是第三种最基本的特征（前两种是 _数据抽象_ 和 _继承_ ）。







### Chp8: 对象的容纳


#### 数组

理解：

> 对数组的大多数必要的介绍已在第4章的最后一节进行。通过那里的学习，大家已知道自己该如何定义及初始化一个数组。对象的容纳是本章的重点，而数组只是容纳对象的一种方式。但由于还有其他大量方法可容纳数组，所以是哪些地方使数组显得如此特别呢？ 有两方面的问题将数组与其他集合类型区分开来：效率和类型。对于Java来说，为保存和访问一系列对象（实际是对象的句柄）数组，最有效的方法莫过于数组。数组实际代表一个简单的线性序列，它使得元素的访问速度非常快，但我们却要为这种速度付出代价：创建一个数组对象时，它的大小是固定的，而且不可在那个数组对象的“存在时间”内发生改变。可创建特定大小的一个数组，然后假如用光了存储空间，就再创建一个新数组，将所有句柄从旧数组移到新数组。这属于“矢量”（Vector）类的行为，本章稍后还会详细讨论它。然而，由于为这种大小的灵活性要付出较大的代价，所以我们认为矢量的效率并没有数组高。
> 
> C++的矢量类知道自己容纳的是什么类型的对象，但同Java的数组相比，它却有一个明显的缺点：C++矢量类的operator[]不能进行范围检查，所以很容易超出边界（然而，它可以查询vector有多大，而且at()方法确实能进行范围检查）。在Java中，无论使用的是数组还是集合，都会进行范围检查——若超过边界，就会获得一个RuntimeException（运行期违例）错误。正如大家在第9章会学到的那样，这类违例指出的是一个程序员错误，所以不需要在代码中检查它。在另一方面，由于C++的vector不进行范围检查，所以访问速度较快——在Java中，由于对数组和集合都要进行范围检查，所以对性能有一定的影响。

**数组和第一类对象**

> 无论使用的数组属于什么类型，数组标识符实际都是指向真实对象的一个句柄。那些对象本身是在内存“堆”里创建的。
> 堆对象既可“隐式”创建（即默认产生），亦可“显式”创建（即明确指定，用一个new表达式）。
> 堆对象的一部分（实际是我们能访问的唯一字段或方法）是只读的length（长度）成员，它告诉我们那个数组对象里最多能容纳多少元素。对于数组对象，“[]”语法是我们能采用的唯一另类访问方法。

```java
//: ArraySize.java
// Initialization & re-assignment of arrays
package c08;

class Weeble {} // A small mythical creature

public class ArraySize {
  public static void main(String[] args) {
    // Arrays of objects:
    Weeble[] a; // Null handle
    Weeble[] b = new Weeble[5]; // Null handles
    Weeble[] c = new Weeble[4];
    for(int i = 0; i < c.length; i++)
      c[i] = new Weeble();
    Weeble[] d = {
      new Weeble(), new Weeble(), new Weeble()
    };
    // Compile error: variable a not initialized:
    //!System.out.println("a.length=" + a.length);
    System.out.println("b.length = " + b.length);
    // The handles inside the array are 
    // automatically initialized to null:
    for(int i = 0; i < b.length; i++)
      System.out.println("b[" + i + "]=" + b[i]);
    System.out.println("c.length = " + c.length);
    System.out.println("d.length = " + d.length);
    a = d;
    System.out.println("a.length = " + a.length);
    // Java 1.1 initialization syntax:
    a = new Weeble[] {
      new Weeble(), new Weeble()
    };
    System.out.println("a.length = " + a.length);

    // Arrays of primitives:
    int[] e; // Null handle
    int[] f = new int[5];
    int[] g = new int[4];
    for(int i = 0; i < g.length; i++)
      g[i] = i*i;
    int[] h = { 11, 47, 93 };
    // Compile error: variable e not initialized:
    //!System.out.println("e.length=" + e.length);
    System.out.println("f.length = " + f.length);
    // The primitives inside the array are
    // automatically initialized to zero:
    for(int i = 0; i < f.length; i++)
      System.out.println("f[" + i + "]=" + f[i]);
    System.out.println("g.length = " + g.length);
    System.out.println("h.length = " + h.length);
    e = h;
    System.out.println("e.length = " + e.length);
    // Java 1.1 initialization syntax:
    e = new int[] { 1, 2 };
    System.out.println("e.length = " + e.length);
  }
} ///:~
Here’s the output from the program:

b.length = 5
b[0]=null
b[1]=null
b[2]=null
b[3]=null
b[4]=null
c.length = 4
d.length = 3
a.length = 3
a.length = 2
f.length = 5
f[0]=0
f[1]=0
f[2]=0
f[3]=0
f[4]=0
g.length = 4
h.length = 3
e.length = 3
e.length = 2
```














---






## 自我充电

### 配置

#### Jar包下载并在intelliJ添加Jar包

[java如何快速下载jar包](https://www.jianshu.com/p/83f89d24db46)
[Intellij IDEA 添加jar包的三种方式](http://zyjustin9.iteye.com/blog/2172445)


### 语言机制

#### 无main函数的class

[没有main函数时的Java程序的执行](http://blog.csdn.net/esonjohn/article/details/64444117)
[在java中和main方法并列的方法为什么一定要加static? ](https://www.zhihu.com/question/34561787)

#### Java代码执行顺序

[想知道Java代码执行顺序么，Let's go](https://www.jianshu.com/p/55c86e6c5c60)


### 数据结构

#### HashMap和HashTable的区别

[6 Difference Between HashMap And HashTable : Popular Interview Question In Java With Example](http://javahungry.blogspot.com/2014/03/hashmap-vs-hashtable-difference-with-example-java-interview-questions.html)
[Differences between HashMap and Hashtable?](https://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable)
[Java 集合--Map、HashMap、HashTable、TreeMap](http://zzqrj.iteye.com/blog/841782)

#### ArrayList vs. LinkedList vs. Vector

[ArrayList vs. LinkedList vs. Vector](https://www.programcreek.com/2013/03/arraylist-vs-linkedlist-vs-vector/)

#### Java中如何遍历Map对象的4种方法

[Java中如何遍历Map对象的4种方法](http://blog.csdn.net/tjcyjd/article/details/11111401)

#### 如何重置一个ArrayList--clear vs removeAll

[如何重置一个ArrayList--clear vs removeAll](https://yemengying.com/2015/10/26/%E8%AF%91-%E5%A6%82%E4%BD%95%E9%87%8D%E7%BD%AE%E4%B8%80%E4%B8%AAArrayList-clear-vs-removeAll/)


### 结构

#### extends和implements的区别

[浅谈java中extends与implements的区别](https://jeffjade.com/2015/05/11/2015-05-11-java-extends-implement/)


### 算法

#### 排序

[掌握Java-Array/List排序](https://mushanshitiancai.github.io/2016/07/03/java/language/%E6%8E%8C%E6%8F%A1Java-Array-List%E6%8E%92%E5%BA%8F/)

