---
tags:
  - java基础
  - 笔记
aliases:
  - java学习
updated: 2026-06-11T17:23:00
---
# 📑 目录

- [[java基础#1.变量|1. 变量]]
  - [[java基础#数据类型：|数据类型]]（基本数据类型 / 引用数据类型）
  - [[java基础#字符类型|字符类型]]（ASCII、Unicode、UTF-8）
  - [[java基础#布尔类型|布尔类型]]
- [[java基础#2.自动类型转换|2. 自动类型转换]]
  - [[java基础#基本数据类型转换|基本数据类型转换]]（自动转换 / 强制转换）
  - [[java基础#基本类型和String类型转换|基本类型和 String 类型转换]]
  - [[java基础#引用类型转换|引用类型转换]]（向上转型 / 向下转型 / instanceof）
- [[java基础#3.修饰符|3. 修饰符]]
  - [[java基础#1.非访问修饰符：|非访问修饰符]]（final / static / abstract / synchronized）
  - [[java基础#2.==访问修饰符==：|访问修饰符]]（public / protected / 默认 / private）
- [[java基础#4.运算符|4. 运算符]]
  - [[java基础#instanceof 运算符|instanceof 运算符]]
- [[java基础#5.正则表达式|5. 正则表达式]]
- [[java基础#6.数组|6. 数组]]
  - [[java基础#三种使用方式|三种使用方式]]（动态初始化 / 静态初始化）
  - [[java基础#数组赋值机制：|数组赋值机制]]（引用赋值）
- [[java基础#7.面向对象|7. 面向对象]]
  - [[java基础#（1）对象内存分布|对象内存分布]]
  - [[java基础#（2）属性|属性]]
  - [[java基础#（3）方法传参机制|方法传参机制]]
  - [[java基础#（4）重载vs重写|重载 vs 重写]]
  - [[java基础#（5）可变参数|可变参数]]
  - [[java基础#（6）构造器|构造器]]
  - [[java基础#（7）this关键字|this 关键字]]
  - [[java基础#（8）super关键字|super 关键字]]
  - [[java基础#（9）包的命名|包的命名]]
  - [[java基础#(10)==封装==|封装]]
  - [[java基础#(11)继承|继承]]
  - [[java基础#(12)多态|多态]]（动态绑定机制）
  - [[java基础#(13)接口|接口]]（接口特性 / 抽象类与接口区别 / 默认方法 / 静态方法）
  - [[java基础#(14)内部类|内部类]]（局部内部类 / 匿名内部类 / 成员内部类 / 静态内部类）
  - [[java基础#（15）类静态成员|类静态成员]]（类变量 / 类方法）
- [[java基础#8.枚举|8. 枚举]]
  - [[java基础#两种实现方式|两种实现方式]]（自定义类 / enum 关键字）
- [[java基础#9.注解|9. 注解]]
  - [[java基础#三个基本注解|三个基本注解]]（@Override / @Deprecated / @SuppressWarnings）
  - [[java基础#四种元注解(Annotation)|四种元注解]]（@Retention / @Target / @Documented / @Inherited）
- [[java基础#10.异常处理|10. 异常处理]]
  - [[java基础#1.异常|异常分类]]（Error / Exception）
  - [[java基础#2.五大常见运行时异常|五大常见运行时异常]]
  - [[java基础#3.异常处理方式：|异常处理方式]]（try-catch-finally / throws）
  - [[java基础#4.自定义异常|自定义异常]]
- [[java基础#11.常用类|11. 常用类]]
  - [[java基础#1. String 类|String 类]]（StringBuilder / StringBuffer 对比）
  - [[java基础#2. Math 类|Math 类]]
  - [[java基础#3. Arrays 类（数组工具类）|Arrays 类]]
  - [[java基础#4. System 类|System 类]]
  - [[java基础#5. BigInteger 与 BigDecimal|BigInteger 与 BigDecimal]]
  - [[java基础#6. 日期时间类（Java 8+）|日期时间类]]（Java 8+ java.time）
  - [[java基础#7. Objects 类|Objects 类]]
  - [[java基础#8. Random 类|Random 类]]
- [[java基础#12.集合|12. 集合]]
  - [[java基础#1. 集合框架概览|集合框架概览]]（List / Set / Map）
  - [[java基础#2. Collection 接口常用方法|Collection 常用方法]]
  - [[java基础#3. List 接口|List 接口]]（ArrayList / LinkedList / Vector 对比）
  - [[java基础#4. Set 接口|Set 接口]]（HashSet / LinkedHashSet / TreeSet）
  - [[java基础#5. Map 接口|Map 接口]]（HashMap / LinkedHashMap / TreeMap / Hashtable）
  - [[java基础#6. Collections 工具类|Collections 工具类]]
  - [[java基础#7. Comparable 与 Comparator|Comparable 与 Comparator]]
  - [[java基础#8. fail-fast 与 fail-safe|fail-fast 与 fail-safe]]
- [[java基础#13.线程|13. 线程]]
  - [[java基础#1. 线程的创建方式|线程创建方式]]（Thread / Runnable / Callable）
  - [[java基础#2. 线程生命周期（6 种状态）|线程生命周期]]（6 种状态）
  - [[java基础#3. 线程常用方法|线程常用方法]]
  - [[java基础#4. 线程同步（synchronized）|线程同步]]（synchronized）
  - [[java基础#5. Lock 锁（java.util.concurrent.locks）|Lock 锁]]（synchronized vs Lock）
  - [[java基础#6. 线程间通信|线程间通信]]（wait/notify / Condition）
  - [[java基础#7. 线程池（ExecutorService）|线程池]]（ThreadPoolExecutor / 拒绝策略）
  - [[java基础#8. volatile 关键字|volatile 关键字]]
  - [[java基础#9. ThreadLocal|ThreadLocal]]
  - [[java基础#10. 死锁|死锁]]（四条件 / jstack 排查）
  - [[java基础#11. 线程安全集合（JUC）|线程安全集合]]（JUC）
- [[java基础#14.IO流原理|14. IO 流原理]]
  - [[java基础#1.流的分类|流的分类]]（字节流 / 字符流 / 输入流 / 输出流）
  - [[java基础#2. File 类（文件操作）|File 类]]
  - [[java基础#3. 字节流（InputStream / OutputStream）|字节流]]
  - [[java基础#4. 字符流（Reader / Writer）|字符流]]
  - [[java基础#5. 缓冲流（Buffered）—— 性能提升|缓冲流]]
  - [[java基础#6. 转换流（InputStreamReader / OutputStreamWriter）|转换流]]
  - [[java基础#7. 对象流 / 序列化（ObjectInputStream / ObjectOutputStream）|序列化]]
  - [[java基础#11. try-with-resources（自动关闭资源）|try-with-resources]]
  - [[java基础#12. 随机访问流（RandomAccessFile）|RandomAccessFile]]
  - [[java基础#13. NIO 基础（Java 7+ java.nio.file）|NIO]]
- [[java基础#15. 反射（Reflection）|15. 反射（Reflection）]]
  - [[java基础#1. 反射的核心类|核心类]]
  - [[java基础#10. 反射的应用场景|应用场景]]
  - [[java基础#11. 反射的优缺点|优缺点]]
- [[java基础#16. Lambda 表达式（Java 8+）|16. Lambda 表达式]]
- [[java基础#17. Stream API（Java 8+）|17. Stream API]]

---

# 关键字
[[java关键字]]
# 1.变量
## 数据类型：
### 基本数据类型：
- 整数类型（4种）：**byte（1字节）**、**short（2字节）**、**int（4字节）**、**long（8字节）**
- 浮点数类型（2种）：**float（4字节）**、**double（8字节）**
- 字符型（1种）：**char（2字节）**
- 布尔型（1种）：**boolean（1字节）**

### 引用数据类型：
- 类(class)：
- 接口(interface)：
- 数组([])：

### 字符类型
字符型在java中本质是整数，在输出时，是unicode码对应的字符

#### 字符编码：
- ASCII码：一个字节表示 128个字符
- uicode：固定大小的编码表 英文和中文都是两个字节表示
- utf-8：大小可变的编码表 英文一个字节、中文三个字节

### 布尔类型
不可以0或非0表示false和true


# 2.自动类型转换
## 基本数据类型转换
![[基本数据类型转换.png]]
*注意：*
1. 多种类型数据混合运算时，系统首先自动将所有数据转换为容量最大的数据类型，在进行计算
2. 精度大（容量大）的数据类型赋值给精度小（容量小）的数据类型 **==会报错==**，反之，会进行自动类型转换
3. （byte，short）和char之间不会相互自动转化。
4. byte，short，char三者间可以计算，在计算时首先转换为int类型
5. boolen不参与转换
6. 自动提升原则：表达式结果的类型自动转为操作数中最大的类型

例：
```java
byte b  = 16;
short s = 14;
short t = s + b;//错误，byte，short，char在计算时首先转换为int类型,不能把int赋值给short
```


### 自动转换（隐式转换）
```java
//小范围 → 大范围，自动转，安全无报错

byte < short < int < long < float < double 
char 可自动转 int
```
### 强制转换（显式转换）
```java
//大范围 → 小范围，必须强转，会丢失精度 / 溢出
int n1 = (int)1.9;

//强转符号只针对最近的操作数有效，往往会使用小括号提升优先级
int x = (int)10 * 3.5 + 6 * 1.5 //报编译错误，double->int
int y = (int)(10 * 3.5 + 6 * 1.5)

```
char类型可以保存int常量值，但不能保存int变量值，这里需要强转


## 基本类型和String类型转换
### 基本类型转String类型
语法：将基本类型的指+"" 即可
### String类型转基本类型
语法：通过基本类型的包装类调用parseXX方法即可
注：
字符串转为字符含义是指把字符串的第一个字符得到
![[基本类型和String类型转换.png]]
## 引用类型转换
[[java基础#10.多态]]
### 向上转型
必须是**继承关系**才能转
1) 本质：父类的引用指向了子类的对象
2) 编译看父类，运行看子类（可以调用父类的所有成员，需要遵守访问权限，但是不能调用子类的特有成员）
```java
Animal animal = new Dog();
```
### 向下转型
1) 只能强转父类的引用，不能强转父类的对象
2) 要求父类的引用必须指向的是当前目标类型的对象
3) 向下转型后，可以调用子类类型中所有的成员
```java
if(animal instanceof Dog){
    Dog dog = (Dog) animal;
}
```
==*注：instanceof比较符用于判断对象的运行类型是否是xx类型或者xx类型的子类型*==
例：[[java基础#instanceof 运算符]]
```java
class AA{}//父类
class BB extends AA {}//子类
public class Test{
	public static void main(String argsp[]){
		AA aa = new BB();
		System.out.print(aa instanceof AA);//true
		System.out.print(aa instanceof BB);//true
		
		Object obj = new Object();
		System.out.print(obj instanceof AA);//false
		
		
	}
}

```
# 3.修饰符
## 1.非访问修饰符：

|     |     关键字      | 核心含义 |     修饰对象      |      关键点       |
| :-: | :----------: | :--: | :-----------: | :------------: |
|     |    final     | 不可变  |    类、方法、变量    | 不能继承、不能重写、不能修改 |
|     |    static    | 属于类  | 变量、方法、代码块、内部类 |  全局唯一，类名直接调用   |
|     |   abstract   | 未实现  |     类、方法      |  不能实例化，必须子类实现  |
|     | synchronized | 线程同步 |    方法、代码块     |   多线程排队，保证安全   |

一个类不能同时被 abstract 和 final 修饰。如果一个类包含抽象方法，那么该类一定要声明为抽象类，否则将出现编译错误。
抽象类可以包含抽象方法和非抽象方法。
## 2.==访问修饰符==：

### 1. 类与成员的访问权限
 default, public , protected, private
- 父类中声明为 public 的方法在子类中也必须为 public。
- 父类中声明为 protected 的方法在子类中要么声明为 protected，要么声明为 public，不能声明为 private。
- 父类中声明为 private 的方法，不能够被子类继承。
### 2. 四种权限（范围从大→小）

|     | 修饰符                   | 访问范围             |
| --- | --------------------- | ---------------- |
|     | `public`（公共）          | 任意包、任意类都能访问      |
|     | `protected`（受保护）      | 本类 + 同包类 + 不同包子类 |
|     | **默认（缺省 / 包访问，无关键字）** | 仅**同一个包**内可用     |
|     | `private`（私有）         | **只能本类内部访问**     |

### 3. 作用区分
#### ① 修饰「类本身」
- 顶层类：只能用 `public` / **默认**，不能用 `protected、private`
- 内部类：四种权限全都可以修饰

#### ② 修饰成员（属性、方法、构造器）
**四种权限全部可用**。

# 4.运算符

## instanceof 运算符
该运算符用于操作对象实例，检查该对象是否是一个特定类型（类类型或接口类型）。
instanceof运算符使用格式如下：
```
( Object reference variable ) instanceof  (class/interface type)
```
如果运算符左侧变量所指的对象，是操作符右侧类或接口(class/interface)的一个对象，那么结果为真。
下面是一个例子：
```
String name = "James";
boolean result = name instanceof String; // 由于 name 是 String 类型，所以返回真
```
# 5.正则表达式

在其他语言中，**\\** 表示：**我想要在正则表达式中插入一个普通的（字面上的）反斜杠，请不要给它任何特殊的意义。**

在 Java 中，**\\** 表示：**我要插入一个正则表达式的反斜线，所以其后的字符具有特殊的意义。**

所以，在其他的语言中（如 Perl），一个反斜杠 \ 就足以具有转义的作用，而在 Java 中正则表达式中则需要有两个反斜杠才能被解析为其他语言中的转义作用。也可以简单的理解在 Java 的正则表达式中，两个\\\代表其他语言中的一个 \，这也就是为什么表示一位数字的正则表达式是 \\\d，而表示一个普通的反斜杠是 \\\。


# 6.数组
**数组是引用类型**
## 三种使用方式
动态初始化
1. 数据类型 数组名[] = new 数据类型[大小]
```java
int a[] = new int[6];
```
2. 先声明，再创建
声明：数据类型 数组名[];
创建:：数组名=new 数据类型[大小];
```java
int a[];
a = new int[10];
```
3. 静态初始化

数据类型 数组名[] = {元素值,元素值,...}
```java
int a[] = {1,23,3,45};
```

## 数组赋值机制：
### 引用赋值
数组在默认情况下是引用传递，赋的值是地址，赋值方式是引用赋值
```java
int[] n1 = {1, 2,3};  
int[] n2;  
n2 = n1;  
for (int j : n2) {  
    System.out.print(j);  
}  
n1[2] = 6;  
System.out.print("\n");  
for (int j : n2) {  
    System.out.print(j);  
}
```
![引用赋值](picture/java/数组执行结果.png)

# 7.面向对象
1. 类是抽象的，代表一类事物，是数据类型
2. 对象是具体的，是实例
3. 类是对象的一个模板，对象是类的一个个体，对应一个实例
## （1）对象内存分布
![对象内存分布](picture/java/对象内存分布.png)
## （2）属性
语法： 访问修饰符 属性类型  属性名；
## （3）方法传参机制
基本数据类型，传递的是值（值拷贝），形参的任何改变不影响实参
引用类型，传递到是地址，形参可以改变实参

## （4）重载vs重写

|     | 对比项重载 | (Overload) | 重写 (Override)  |
| :-: | :---: | :--------: | :------------: |
|     |  位置   | 同一个类 / 父子类 |    仅子类 & 父类    |
|     |  方法名  |    必须相同    |      必须相同      |
|     | 参数列表  |    必须不同    |     必须完全相同     |
|     |  返回值  |    无要求     | 基本类型必须一致，引用可协变 |
|     | 访问修饰符 |    无要求     |   子类权限 ≥ 父类    |
|     |  异常   |    无要求     |    异常范围不能扩大    |
|     | 绑定时机  |  编译期（静态）   |    运行期（动态）     |
|     |  关键字  |   无注解要求    | 推荐加 @Override  |

## （5）可变参数
语法：
```java
访问修饰符 返回类型 方法名（数据类型... 形参名）{
}

//例如
public int sum(int... nums){
	int res = 0;
	for(int i = 0; i < nums.lengtj; i++){
		res += nums[i];
	}
	return res;
}
```
- 可变参数可以是数组；
- 可变参数本质是数组；
- 可变参数可以和普通参数放到一起，但必须保证可变参数在最后；
- 一个形参列表中只能出现一个可变参数；

## （6）构造器
也就是c++的构造函数
- 没有返回值，也不能写void
- 构造器名称和类名称一样
- 构造器形参列表规则和成员方法一样
- 构造器可以重载
- 注意事项
	- 构造器是完成对象初始化，并不是创建对象
	- 创建对象时，自动调用构造方法
	- 如果程序员没有定义构造器，系统会自动生成一个默认无参构造器，如果定义，则会覆盖，除非显式的定义一下

`javap 是JDK提供的一个命令行工具，javap能对给定的class文件提供的字节代码进行反编译`

## （7）this关键字
this代表当前对象，使用this解决前面变量命名问题

## （8）super关键字
super代表父类的引用，用于访问父类的属性、方法、构造器
1. 访问父类的属性，但是不能访问private属性
2. 访问父类的方法，但是不能访问private方法
3. 访问父类的构造器
## （9）包的命名
命名规则：
- 只能包含数字、字母、下划线、小圆点，但不能使用数字开头，不能是关键字或保留字
- 一般是com.公司名.项目名.业务模块名
## (10)==封装==
封装就是把抽象出的数据（属性）和对数据的操作（方法）封装在一起，数据被保护在内部，程序其他部分只有通过被授权的操作（方法），才能对数据进行操作。
步骤：
- 私有化属性
- 设置公共set方法，对属性判断并赋值
- 设置公共get方法，获取属性的值
## (11)继承
extends 关键字
1. 子类继承了所有的属性和方法，==非私有的属性和方法可以在子类直接访问==，但是私有属性和方法不能再子类直接访问，要通过父类提供的公共方法去访问
2. 子类必须调用父类的构造器，完成父类的初始化
3. 先创建父类，再创建子类；如果父类没有无参构造器，必须用super指明用哪个构造器完成对父类的初始化工作，否则，编译不通过
4. 如希望指定调用父类的某个构造器，需要显示调用super()
5. super和this在使用时都只能放在构造器的第一行，因此两个方法不能共存在一个构造器中，指的是super()和this()
6. java所有类是Object类的子类，Object是所有类的基类
7. 父类构造器的调用不限于直接父类，将一直往上追溯直到Object类
8. 子类最多只能继承一个父类，即java是单继承
9. 不能滥用继承，子类和父类之间必须满足is a关系，即子类 is a 父类

继承中，依据查找关系来返回信息的：
		1. 首先看子类是否有该属性，如果有且可以访问，则返回信息
		2. 如果子类没有，则看父类（看父类是否有该属性，如果有且可以访问，则返回信息。。。）
		3. 如果父类没有，按照2的规则，继续向上查找，知道Object类

## (12)多态
- 方法的多态：
	1. 重载和重写

- 对象的多态：[[java基础#引用类型转换]]
	1. 一个对象的编译类型和运行类型可以不一致
	2. 编译类型在定义对象时就确定了，不能改变
	3. 运行类型可以改变
	4. 编译类型看定义时=的左边，运行类型看=的右边


属性没有重写一说，属性的值看编译类型
```java
public class Test{
	public static void main(String args[]){
		Base base = new Sub();
		System.out.print(base.count);
	}
}
class Base{
	int count=10;
}

class Sub extends Base{
	int count=20;
}

//运行结果为10，属性没有重写一说，属性的值看编译类型
```


### 1.动态绑定机制
当调用对象方法时，该方法回合该对象的内存地址/运行类型绑定
当调用对象属性时，没有动态绑定机制，哪里声明，那里使用
## (13)接口

是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

### 1.接口与类相似点：

- 一个接口可以有多个方法。
- 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
- 接口的字节码文件保存在 .class 结尾的文件中。
- 接口相应的字节码文件必须在与包名称相匹配的目录结构中。

### 2.接口与类的区别：

- 接口不能用于实例化对象。
- 接口没有构造方法。
- 接口中所有的方法必须是抽象方法，Java 8 之后 接口中可以使用 default 关键字修饰的非抽象方法。
- 接口不能包含成员变量，除了 static 和 final 变量。
- 接口不是被类继承了，而是要被类实现。
- 接口支持多继承。

### 3.接口特性
- 接口中每一个方法也是隐式抽象的,接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）。
- 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
- 接口属性访问形式：接口名.属性名（这表明，接口里的属性是静态的）
- 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。


#### 接口训练：
```java

package com.example.demo;  
  
public class InterfaceExercise {  
    public static void main(String[] args) {  
        B b = new B();  
        System.out.println(B.a);  //23
        System.out.println(A.a);  //23
        System.out.println(b.a);  //23
    }  
}  
  
class B implements A {  
  
}  
  
interface A {  
    int a = 23;  
}

```
==注：同一个源文件：只能 1 个 public 类 / 接口，其他类只能默认访问权限==

### 4.抽象类和接口的区别

- 1. 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。
- 2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。
- 3. 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
- 4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

### 5. 接口默认方法（Java 8+）与静态方法

#### 为什么引入默认方法？
为了向后兼容：当需要给现有接口（如 `Collection`、`List`）添加新方法时，不会破坏已有的实现类。

#### 默认方法（default）
```java
interface Vehicle {
    void run();  // 抽象方法（实现类必须实现）

    // 默认方法：接口中直接提供实现，实现类可选择不重写
    default void honk() {
        System.out.println("车辆鸣笛：嘟嘟！");
    }
}

class Car implements Vehicle {
    @Override
    public void run() {
        System.out.println("汽车在行驶");
    }
    // honk() 可以不重写，直接继承默认实现
}
```

#### 静态方法（static）
```java
interface MathUtils {
    static int add(int a, int b) {
        return a + b;
    }
}
// 调用：MathUtils.add(1, 2);  直接通过接口名调用
```

#### 默认方法的冲突解决规则

当一个类实现多个接口，且这些接口有相同签名的默认方法时，遵循以下规则：

|     | 优先级 | 规则                                          |
| :-: | :-: | :------------------------------------------ |
|     |  1  | **类中的方法优先**：子类中显式定义的方法优先级最高                 |
|     |  2  | **子接口优先**：如果两个接口存在继承关系，子接口的默认方法优先           |
|     |  3  | **必须手动覆盖**：两个无关接口冲突时，实现类必须 `@Override` 解决冲突 |

```java
interface A {
    default void hello() { System.out.println("A"); }
}
interface B {
    default void hello() { System.out.println("B"); }
}
// 冲突：必须手动覆盖
class MyClass implements A, B {
    @Override
    public void hello() {
        A.super.hello();  // 选择调用 A 的默认方法
    }
}
// 类优先于接口：父类的方法会屏蔽接口默认方法
class Base { public void hello() { System.out.println("Base"); } }
class Child extends Base implements A { }  // 继承 Base.hello()，A 的默认方法被忽略
```

**注**：JDK 1.9 以后，允许将接口中方法定义为 `private`，使得某些复用的代码不会把方法暴露出去。

> 📖 更多接口增强内容（默认方法冲突解决、私有接口方法）见 [[java高级#6. 接口增强|java高级 → 接口增强]]。



## (14)内部类
类的五大成员
属性、方法、构造器、代码块、内部类
内部类分为四种：
1. 定义在外部类局部位置上：（比如方法内）
	1. 局部内部类（有类名)
	2. ==匿名内部类（没有类名）（重点）==
2. 定义在外部类的成员位置上：
	1. 成员内部类（没用static修饰）
	2. 静态内部类（用static修饰）


### 1.局部内部类：
1. ==局部内部类定义在方法或代码块中==
2. 可以直接访问外部类的所有成员，包括私有的
3. 不能添加访问修饰符，但是可以加final（不被继承）
4. ==作用域仅在定义它的方法内或代码块内==
5. 局部内部类可以直接访问外部类的成员
6. 外部类在方法中，可以创建Inner02对象，然后调用
7. 外部其他类不能访问局部内部类（局部内部类地位是局部变量）
8. 外部类和局部内部类成员重名，遵循就近原则，如果想访问外部类成员，使用==*外部类名.this.成员*==  
```java
public class LocalInnerClass {  
    public static void main(String[] args){  
        Outer02 outer02= new Outer02();  
        outer02.m1();  
    }  
}  
  
class Outer02 {  //外部类
    private  int n = 100;  
    public void m2() {  
        System.out.println("Outer02 m2");  
    }  
    public  void m1() {  
        class Inner02 {  方法中的局部内部类，相当于局部变量
            private int n = 200;  
            public void f1() {  
                System.out.println("Inner02类的成员n " + n);  
                //Outer02.this相当于外部类的对象，谁调用了m1的方法，Outer02.this就指向谁  
                System.out.println("Outer02类的成员n " + Outer02.this.n);  
                m2();//内部类可以直接访问外部类的成员  
            }  
        }  
  
        class Inner03 extends Inner02 {  
  
        }  
  
        Inner02 i = new Inner02();//外部类访问内部类，需要创建对象再访问  
        i.f1();  
    }  
}
```
###  ==2.匿名内部类（重点）==
基本语法：
```java
new 类/接口名(参数列表){
	类体
}
```
1. 本质是类，该类没有名字（匿名内部类的名字我们看不到，但系统会给他一个名字）；==同时还是一个对象==
2. 匿名内部类是定义在外部类中的局部位置，比如方法中
3. 用于简化开发，某些接口只需要用一次，后续不用，传统基于接口创建类，实例化有些啰嗦，而用==匿名内部类只使用一次，后续不能再用==

示例：
```java
package com.example.demo.InnerClass;  
  
public class AnonymousInnerClass {  
    public static void main(String[] args){  
        Outer04 outer04 = new Outer04();  
        outer04.method();  
    }  
}  
  
class Outer04{  
    private int num = 10;  
  
    public void  method() {  
        //基于接口的匿名内部类  
        /*  
        a的编译类型是A02  
        运行类型是Outer04$1  
         */        A02 a = new A02(){  
            @Override  
            public void cry() {  
                System.out.println("hello");  
            }  
        };  
        System.out.println("a的运行类型" + a.getClass());  
        a.cry();  
  
        //基于类的匿名内部类  
        Father father = new Father("jack") {  
            @Override  
            public void test(){  
                System.out.println("匿名内部类的test（）方法");  
            }  
        };//加{}运行类型会变为Outer04$2  
        //不加，运行类型是Father  
        System.out.println("father的运行类型" + father.getClass());  
        father.test();  
  
    }  
}
interface A02 {  
    public void cry();  
}  
  
class Father {  
    public Father(String name){  
    }  
    public void test(){  
  
    }  
}
```

### 3. 成员内部类
定义在外部类的成员位置，没用static修饰，可以访问外部类的所有成员，包含私有的
1. 作用域和外部类的其他成员一样，为==整个类体==
2. 外部类和局部内部类成员重名，遵循就近原则，如果想访问外部类成员，使用==*外部类名.this.成员*==  
### 4.静态内部类
定义在外部类的成员位置，并且有static修饰，可以访问外部类的所有成员，包含私有的，但是不能直接访问非静态成员
1. 作用域和外部类的其他成员一样，为==整个类体==
2. 外部类和局部内部类成员重名，遵循就近原则，如果想访问外部类成员，使用==*外部类名.成员*==  

## （15）类静态成员
### 1. 类变量（静态变量）
最大特点是被类的所有对象实例共享
static类变量在类加载时就生成了

定义：
	- ==访问修饰符 static 数据类型 变量名（推荐）==
	- static 访问修饰符 数据类型 变量名
访问方式：
	- ==类名.类变量名（推荐）==
	- 对象名.类变量名

### 2. 类方法（静态方法）
- 定义：
	- ==访问修饰符 static 数据类型 方法名（推荐）==
	- static 访问修饰符 数据类型 方法名

- 访问方式：
	- ==类名.类方法名（推荐）==
	- 对象名.类方法名

- 经典使用场景：
方法中不涉及任何对象的成员，可以设计成类方法，提高开发效率，即==不需要创建对象就可以使用==

- 注意事项：
	- 类方法和普通方法一样，都是随着类的加载而加载，将结构信息存储在方法区
	- 类方法中不允许使用和对象相关的关键字，this、super
	- 类方法只能访问类变量（静态变量）、类方法（静态方法），普通方法既可以访问普通变量、方法，也可以访问静态变量、方法



# 8.枚举
枚举是一组常量的集合，可以这样理解：枚举属于一种特殊的类，里面只包含一组有限的特定的对象
## 两种实现方式
1) 自定义类实现枚举
	- 第一步，将构造器私有化，目的防止直接new
	- 第二步，去掉set方法，防止属性被修改
	- 第三步，直接实例化固定对象
	- 可以优化，加入final修饰符
2) 使用enum关键字实现枚举
	- 使用关键字enum替代class
	- 通常将定义常量对象写在前面，枚举类的对象必须写在行首
	- 如果使用无参构造器创建常量对象，则可以简化后面的()

示例：
```java
public class EnumClassExercise01 {  
    public static void main(String[] args){  
        System.out.println(Season.SPRING.toString());  
  
    }  
}  
  
  
enum Season {  
    SPRING("春天","温暖"),SUMMER("夏天","炎热"),  
    AUTUMN("秋天","凉爽"),WINTER("冬天","寒冷");  
    private final String seasonName;  
    private final String seasonDesc;  
  
  
    private Season(String seasonName,String seasonDesc){  
        this.seasonName = seasonName;  
        this.seasonDesc = seasonDesc;  
    }  
  
    public String getSeasonName(){  
        return seasonName;  
    }  
  
    public String getSeasonDesc(){  
        return seasonDesc;  
    }  
  
    @Override  
    public String toString() {  
        return "seasonName=" + seasonName + " seasonDesc=" + seasonDesc;  
    }  
}
```
# 9.注解
也被称为元数据（Metadata)，用于修饰解释包、类、方法、属性、构造器、局部变量等数据信息
### 三个基本注解
@interface 表明是注解类，这个不是interface
1. @Override：限定某个方法，是重写赴俄历方法，该注解只能用于方法
	1. 加了该注解，编译器就好检查是否真的重写，如果没有，则编译报错
2. @Deprecated：用于表示某个程序元素（类、方法等）已过时，==即不再推荐使用，但任然可以使用==
3. @SuppressWarnings：抑制编译器警告

- @SuppressWarnings（{“”}）：大括号里可以写入希望抑制（不显示）的警告信息
- 作用范围和放置位置有关
### 四种元注解(Annotation)
1. @Retention//指定注解作用范围（SOURCE、CLASS、RUNTIME）
只能用于修饰一种Annotation定义，用于指定该Annotation可以保留多长时间
![@Retention三种值](../../../picture/java/@Retention三种值.png)
2. @Target//指定注解可以在哪些地方使用
用于修饰Annotation定义，用于指定被修饰的Annotation能用于修改哪些程序元素

3. @Documented//指定该注解是否会在javadoc中体现
4. @Inherited//子类会继承父类
# 10.异常处理
程序执行中发生的不正常情况称为“异常”。（语法错误和逻辑错误不是异常）
## 1.异常
![异常类层级图](../../../picture/java/异常类层级图.png)
异常分为两类：
1) Error(错误)：java虚拟机无法解决的严重问题。如JVM系统内部错误、资源耗尽。
Error是严重错误，程序会崩溃

2) Exception: 其他因编程错误或偶然的外在因素导致的一般性问题，可以使用针对性的代码进行处理。例如空指针访问，试图读取不存在的文件，网络中断等等
Exception分为两大类：运行时异常、编译时异常

## 2.五大常见运行时异常
### 1）NullPointerException (空指针异常)
需要使用对象的地方使用了null
```java
public class NullPointerException {  
    public static void main(String[] args){  
        String str = null;  
        System.out.println(str.length());  
    }  
}
```
![NullPointerException.png](../../../picture/java/NullPointerException.png)
### 2) ArithmeticException (数学运算异常)
比如整数除以零
### 3) ArrayindexOutofBoundsException (数组下标越界异常)
用非法索引访问数组时抛出的异常
### 4) ClassCastException (类型转换异常)
当试图将对象强转为不是实例的子类时，抛出该异常
### 5)NumberFormatException (数字格式不正确异常)
当程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常

## 3.异常处理方式：
### 1. try-catch-finally
程序员在代码中捕获发生的异常，自行处理
语法：
```java
try {
	可疑代码；
	将异常生成对应的异常对象，传递给catch块
} catch(异常) {
	对异常的处理
}
//如果没有finally，语法可以通过
```
- finally块无论异常是否发生，都会执行
- 可以有多个catch语句，捕获不同的异常，要求父类异常在后，子类异常在前，比如（Exception在后，NullPointerException在前），如果发生异常，只会匹配一个catch块
### 2. throws
将发生的异常抛出，交给调用者（方法）来处理，最顶级的处理者就是JVM

### 3.异常处理细节
1) 编译异常，程序中必须处理，比如try-catch或者throws
2) 运行时异常，程序中如果没有处理，默认为throws的方式处理
3) 子类重写父类方法时，对抛出异常的规定：抛出异常类型要么和父类异常类型一致，要么为父类抛出异常类型的子类型
## 4.自定义异常
定义类继承Exception或RuntimeException
如果继承Exception，属于编译异常
如果继承RuntimeException，属于运行异常

# 11.常用类

## 1. String 类
- String 对象不可变（final 类），每次修改实际是创建了新对象
- 两种创建方式：
	- `String s = "hello"` → 从常量池中获取
	- `String s = new String("hello")` → 堆中创建新对象

```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");
System.out.println(s1 == s2);       // true，指向常量池同一个对象
System.out.println(s1 == s3);       // false，s3 指向堆中对象
System.out.println(s1.equals(s3));  // true，String 重写了 equals，比较内容
```

### 常用方法

|     | 方法                                                      | 说明                    |
| --- | ------------------------------------------------------- | --------------------- |
|     | `length()`                                              | 获取字符串长度               |
|     | `charAt(int index)`                                     | 获取指定索引处的字符            |
|     | `equals(Object obj)`                                    | 判断字符串内容是否相等           |
|     | `equalsIgnoreCase(String str)`                          | 忽略大小写比较               |
|     | `indexOf(String str)`                                   | 获取子串第一次出现的索引，找不到返回 -1 |
|     | `substring(int begin, int end)`                         | 截取子串（左闭右开）            |
|     | `trim()`                                                | 去除首尾空格                |
|     | `replace(char old, char new)`                           | 替换字符/字符串              |
|     | `split(String regex)`                                   | 按正则表达式分割，返回 String[]  |
|     | `toCharArray()`                                         | 转换为字符数组               |
|     | `startsWith(String prefix)` / `endsWith(String suffix)` | 判断前缀/后缀               |
|     | `contains(CharSequence s)`                              | 是否包含子串                |
|     | `format(String format, Object... args)`                 | 格式化字符串                |

### String、StringBuilder、StringBuffer 对比

|     | 特性   | String  | StringBuilder | StringBuffer     |
| --- | ---- | ------- | ------------- | ---------------- |
|     | 可变性  | 不可变     | 可变            | 可变               |
|     | 线程安全 | —       | 不安全           | 安全（synchronized） |
|     | 效率   | —       | 高             | 较低               |
|     | 适用场景 | 少量字符串操作 | 单线程、大量拼接      | 多线程、大量拼接         |

```java
StringBuilder sb = new StringBuilder();
sb.append("hello").append(" world");  // 链式调用
sb.insert(5, " java");      // 指定位置插入
sb.delete(5, 10);           // 删除 [5, 10) 字符
sb.reverse();               // 反转
System.out.println(sb.toString());
```

## 2. Math 类

常用静态方法：

|     | 方法                                  | 说明                   |
| --- | ----------------------------------- | -------------------- |
|     | `Math.abs(x)`                       | 绝对值                  |
|     | `Math.max(a, b)` / `Math.min(a, b)` | 最大/最小值               |
|     | `Math.pow(a, b)`                    | a 的 b 次方             |
|     | `Math.sqrt(x)`                      | 平方根                  |
|     | `Math.round(x)`                     | 四舍五入                 |
|     | `Math.ceil(x)`                      | 向上取整                 |
|     | `Math.floor(x)`                     | 向下取整                 |
|     | `Math.random()`                     | 返回 [0.0, 1.0) 之间的随机数 |

```java
// 生成 [a, b] 范围的随机整数
int random = (int)(Math.random() * (b - a + 1)) + a;
```

## 3. Arrays 类（数组工具类）

|     | 方法                                  | 说明               |
| --- | ----------------------------------- | ---------------- |
|     | `Arrays.toString(arr)`              | 数组转字符串           |
|     | `Arrays.sort(arr)`                  | 升序排序             |
|     | `Arrays.sort(arr, Comparator)`      | 自定义排序            |
|     | `Arrays.binarySearch(arr, key)`     | 二分查找（需先排序）       |
|     | `Arrays.copyOf(arr, newLength)`     | 复制数组             |
|     | `Arrays.copyOfRange(arr, from, to)` | 复制指定范围           |
|     | `Arrays.fill(arr, value)`           | 填充数组             |
|     | `Arrays.equals(arr1, arr2)`         | 比较数组是否相等         |
|     | `Arrays.asList(...)`                | 将元素转为 List（固定大小） |

```java
int[] arr = {3, 1, 5, 2, 4};
Arrays.sort(arr);                          // [1, 2, 3, 4, 5]
int idx = Arrays.binarySearch(arr, 3);     // 2
int[] copy = Arrays.copyOf(arr, 3);        // [1, 2, 3]
```

## 4. System 类

|     | 方法                                                     | 说明                  |
| --- | ------------------------------------------------------ | ------------------- |
|     | `System.exit(0)`                                       | 退出 JVM              |
|     | `System.currentTimeMillis()`                           | 当前时间戳（毫秒），用于计算耗时    |
|     | `System.arraycopy(src, srcPos, dest, destPos, length)` | 数组拷贝（native 方法，效率高） |
|     | `System.gc()`                                          | 建议 JVM 进行垃圾回收       |
|     | `System.getProperty("key")`                            | 获取系统属性              |

## 5. BigInteger 与 BigDecimal

用于高精度计算，超过基本类型范围。

```java
// BigInteger：任意精度整数
BigInteger bi1 = new BigInteger("123456789123456789");
BigInteger bi2 = new BigInteger("987654321987654321");
BigInteger sum = bi1.add(bi2);
BigInteger product = bi1.multiply(bi2);
BigInteger quotient = bi1.divide(bi2);

// BigDecimal：高精度小数（金融计算首选）
BigDecimal bd1 = new BigDecimal("1.234");
BigDecimal bd2 = new BigDecimal("5.678");
BigDecimal result = bd1.multiply(bd2);
// 除法需指定精度和舍入模式，否则无限小数会抛异常
BigDecimal divResult = bd1.divide(bd2, 2, RoundingMode.HALF_UP);
```

**注意事项**：BigDecimal 用 `String` 构造器或 `valueOf()`，不要用 `double` 构造器（会带入浮点误差）。

## 6. 日期时间类（Java 8+）

Java 8 引入 `java.time` 包，**线程安全、不可变**。核心类：

| 类 | 说明 | 示例 |
|:--:|:----|:----:|
| `LocalDate` | 日期（不含时间） | `LocalDate.now()` |
| `LocalTime` | 时间（不含日期） | `LocalTime.now()` |
| `LocalDateTime` | 日期 + 时间 | `LocalDateTime.now()` |
| `DateTimeFormatter` | 格式化/解析 | `DateTimeFormatter.ofPattern("yyyy-MM-dd")` |
| `Instant` | 时间戳（UTC） | `Instant.now()` |

```java
// 创建
LocalDateTime now = LocalDateTime.now();

// 格式化
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
String formatted = now.format(dtf);

// 日期运算（不可变，返回新对象）
LocalDateTime tomorrow = now.plusDays(1);
```

> 📖 **完整内容见 [[java高级#7. 新日期时间 API（java.time）|java高级 → 日期时间 API]]** 包括：Duration/Period、ZonedDateTime 时区、TemporalAdjusters 日期调整器、旧 API 互转等。

## 7. Objects 类

|     | 方法                                   | 说明                          |
| --- | ------------------------------------ | --------------------------- |
|     | `Objects.equals(a, b)`               | 安全比较（null 安全，a 为 null 不抛异常） |
|     | `Objects.requireNonNull(obj)`        | 非空检查，null 则抛 NPE            |
|     | `Objects.requireNonNull(obj, "msg")` | 带自定义消息的非空检查                 |

## 8. Random 类

```java
Random random = new Random();
int i = random.nextInt();        // 随机整数
int i2 = random.nextInt(100);    // [0, 100) 内的整数
double d = random.nextDouble();  // [0.0, 1.0)
boolean b = random.nextBoolean();
```

# 12.集合

## 1. 集合框架概览

![[java集合框架.png]]

```
Collection（单列集合）
├── List（有序、可重复）
│   ├── ArrayList（数组实现，查询快）
│   ├── LinkedList（链表实现，增删快）
│   └── Vector（线程安全，已基本弃用）→ Stack
├── Set（无序、不可重复）
│   ├── HashSet（哈希表，最快）
│   │   └── LinkedHashSet（链表维护插入顺序）
│   └── TreeSet（红黑树，自动排序）
Map（双列集合，键值对）
├── HashMap（哈希表，键不可重复）
│   └── LinkedHashMap（链表维护插入顺序）
├── TreeMap（红黑树，键自动排序）
└── Hashtable（线程安全，已基本弃用）→ Properties
```

## 2. Collection 接口常用方法

|     | 方法                        | 说明             |
| --- | ------------------------- | -------------- |
|     | `add(E e)`                | 添加元素           |
|     | `remove(Object o)`        | 删除元素（只删第一个匹配项） |
|     | `contains(Object o)`      | 是否包含           |
|     | `size()`                  | 元素个数           |
|     | `isEmpty()`               | 是否为空           |
|     | `clear()`                 | 清空             |
|     | `addAll(Collection c)`    | 批量添加           |
|     | `removeAll(Collection c)` | 批量删除（差集）       |
|     | `retainAll(Collection c)` | 取交集            |
|     | `toArray()`               | 转为 Object[]    |

## 3. List 接口

### ArrayList vs LinkedList vs Vector

|     | 特性   | ArrayList   | LinkedList | Vector           |
| --- | ---- | ----------- | ---------- | ---------------- |
|     | 底层结构 | Object[] 数组 | 双向链表       | Object[] 数组      |
|     | 线程安全 | 不安全         | 不安全        | 安全（synchronized） |
|     | 查询效率 | O(1)        | O(n)       | O(1)             |
|     | 增删效率 | O(n)（需移位）   | O(1)（改指针）  | O(n)             |
|     | 扩容   | 1.5 倍       | 无（链表）      | 2 倍              |

### List 特有方法

|     | 方法                          | 说明        |
| --- | --------------------------- | --------- |
|     | `get(int index)`            | 获取指定索引元素  |
|     | `set(int index, E e)`       | 替换指定位置元素  |
|     | `add(int index, E e)`       | 在指定位置插入   |
|     | `remove(int index)`         | 删除指定位置元素  |
|     | `indexOf(Object o)`         | 首次出现的索引   |
|     | `lastIndexOf(Object o)`     | 最后一次出现的索引 |
|     | `subList(int from, int to)` | 截取子列表     |

### 遍历方式

```java
List<String> list = new ArrayList<>();
// 1. 普通 for
for (int i = 0; i < list.size(); i++) { }
// 2. 增强 for
for (String s : list) { }
// 3. 迭代器（遍历中删除元素必须用此方式）
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    String s = it.next();
    if (条件) it.remove();  // 安全删除
}
// 4. forEach（Java 8）
list.forEach(s -> System.out.println(s));
```

## 4. Set 接口

### HashSet
- 底层是 `HashMap`，元素作为 key，value 是固定的 `PRESENT` 对象
- 无序，不可重复，允许一个 null
- 判断重复：先比较 `hashCode()`，再比较 `equals()`
- **自定义类存入 HashSet 必须重写 `hashCode()` 和 `equals()`**

### LinkedHashSet
- 继承 HashSet，底层是 `LinkedHashMap`
- 维护双向链表，保持插入顺序
- 遍历顺序与插入顺序一致

### TreeSet
- 底层是 `TreeMap`（红黑树）
- 元素自动按**自然顺序**或**自定义 Comparator** 排序
- 不允许 null

```java
// 自然排序（元素需实现 Comparable）
TreeSet<Person> set1 = new TreeSet<>();

// 自定义排序（Comparator）
TreeSet<Person> set2 = new TreeSet<>((p1, p2) -> p1.getAge() - p2.getAge());
```

## 5. Map 接口

### HashMap
- JDK 1.7：数组 + 链表
- JDK 1.8：数组 + 链表/红黑树（链表长度 > 8 且数组长度 ≥ 64 时转红黑树）
- 允许一个 null 键，多个 null 值
- 默认容量 16，负载因子 0.75，扩容为 2 倍
- **key 为自定义类时必须重写 `hashCode()` 和 `equals()`**

### LinkedHashMap
- 继承 HashMap，内部维护双向链表
- 保持插入顺序或访问顺序

### TreeMap
- 红黑树实现
- 按 key 自然顺序或自定义 Comparator 排序

### Hashtable
- 线程安全（方法全部 synchronized），已基本被 **ConcurrentHashMap** 替代
- 不允许 null 键和 null 值

### Map 常用方法

|     | 方法                            | 说明                      |
| --- | ----------------------------- | ----------------------- |
|     | `put(K key, V value)`         | 添加/替换（返回旧值或 null）       |
|     | `get(Object key)`             | 根据键获取值                  |
|     | `remove(Object key)`          | 删除                      |
|     | `containsKey(Object key)`     | 是否包含键                   |
|     | `containsValue(Object value)` | 是否包含值                   |
|     | `size()`                      | 键值对个数                   |
|     | `keySet()`                    | 返回所有 key 的 Set          |
|     | `values()`                    | 返回所有 value 的 Collection |
|     | `entrySet()`                  | 返回所有 Entry 的 Set        |

```java
// 遍历 Map
Map<String, Integer> map = new HashMap<>();

// 方式1：entrySet（推荐，一次取 key 和 value）
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    String key = entry.getKey();
    Integer value = entry.getValue();
}

// 方式2：keySet
for (String key : map.keySet()) {
    Integer value = map.get(key);
}

// 方式3：forEach（Java 8）
map.forEach((k, v) -> System.out.println(k + " = " + v));
```

## 6. Collections 工具类

|     | 方法                                                      | 说明       |
| --- | ------------------------------------------------------- | -------- |
|     | `Collections.sort(list)`                                | 升序排序     |
|     | `Collections.sort(list, Comparator)`                    | 自定义排序    |
|     | `Collections.reverse(list)`                             | 反转       |
|     | `Collections.shuffle(list)`                             | 随机打乱     |
|     | `Collections.max(collection)` / `min()`                 | 最大/最小值   |
|     | `Collections.frequency(collection, obj)`                | 元素出现次数   |
|     | `Collections.replaceAll(list, old, new)`                | 替换所有旧值   |
|     | `Collections.unmodifiableList(list)`                    | 转为不可变集合  |
|     | `Collections.synchronizedList(list)`                    | 转为线程安全集合 |
|     | `Collections.emptyList()` / `emptySet()` / `emptyMap()` | 返回空不可变集合 |

```java
// 转为线程安全的集合（每一方法都加了 synchronized，效率低）
List<String> syncList = Collections.synchronizedList(new ArrayList<>());
// 更推荐使用 JUC 下的并发集合替代
```

## 7. Comparable 与 Comparator

|     | 对比项  | Comparable         | Comparator                     |
| --- | ---- | ------------------ | ------------------------------ |
|     | 位置   | `java.lang`        | `java.util`                    |
|     | 实现方法 | `compareTo(T o)`   | `compare(T o1, T o2)`          |
|     | 排序规则 | 类内部定义（自然排序）        | 外部定义（可多个）                      |
|     | 使用方式 | 类实现该接口             | 匿名内部类 / Lambda                 |
|     | 调用方式 | `Arrays.sort(arr)` | `Arrays.sort(arr, comparator)` |

```java
// Comparable：内部排序
class Person implements Comparable<Person> {
    private int age;
    @Override
    public int compareTo(Person o) {
        return this.age - o.age;  // 升序
    }
}

// Comparator：外部排序（更灵活）
Collections.sort(list, (p1, p2) -> p1.getAge() - p2.getAge());

// 复合排序
list.sort(Comparator.comparing(Person::getAge)
                    .thenComparing(Person::getName));
```

## 8. fail-fast 与 fail-safe

|     | 机制        | 说明                                            | 代表集合                                    |
| --- | --------- | --------------------------------------------- | --------------------------------------- |
|     | fail-fast | 迭代时集合被修改则抛出 `ConcurrentModificationException` | ArrayList, HashMap                      |
|     | fail-safe | 迭代的是原集合的快照，修改不影响遍历                            | CopyOnWriteArrayList, ConcurrentHashMap |

```java
// fail-fast 示例
List<String> list = new ArrayList<>();
list.add("a"); list.add("b");
for (String s : list) {
    list.add("c");  // ❌ ConcurrentModificationException
}
// 正确做法：用 Iterator 的 remove() 或用 CopyOnWriteArrayList
```

# 13.线程

## 1. 线程的创建方式

### 方式一：继承 Thread 类
```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " 正在执行");
    }
}
// 启动
MyThread t = new MyThread();
t.start();  // 调用 start()，不是 run()
```

### 方式二：实现 Runnable 接口（推荐）
```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " 正在执行");
    }
}
// 启动（静态代理模式）
Thread t = new Thread(new MyRunnable());
t.start();

// Lambda 简化
new Thread(() -> System.out.println("线程运行")).start();
```

### 方式三：实现 Callable 接口（有返回值）
```java
class MyCallable implements Callable<String> {
    @Override
    public String call() throws Exception {
        Thread.sleep(1000);
        return "任务执行完毕";
    }
}

// 使用 FutureTask 包装
FutureTask<String> ft = new FutureTask<>(new MyCallable());
new Thread(ft).start();
String result = ft.get();  // 阻塞等待返回值
```

**三种方式对比：**

|     | 方式       | 返回值 | 抛异常 | 使用灵活性       |
| --- | -------- | --- | --- | ----------- |
|     | Thread   | 无   | 不能  | 差（单继承限制）    |
|     | Runnable | 无   | 不能  | 好（可多实现）     |
|     | Callable | 有   | 可以  | 好 + 支持泛型返回值 |

> 📖 Java 8 的 `CompletableFuture`（异步编程与回调编排）见 [[java高级#8. CompletableFuture|java高级 → CompletableFuture]]。

## 2. 线程生命周期（6 种状态）

```
NEW → RUNNABLE → TERMINATED
         ↓
      BLOCKED（等锁）
      WAITING（wait/join/park，无限期等待）
      TIMED_WAITING（sleep/wait(timeout)/join(timeout)，有限等待）
```

|     | 状态            | 说明                            |
| --- | ------------- | ----------------------------- |
|     | NEW           | 创建了线程对象，还未 start()            |
|     | RUNNABLE      | 正在 JVM 中运行（就绪 + 运行）           |
|     | BLOCKED       | 等待获取锁（synchronized）           |
|     | WAITING       | 无限期等待（wait、join 无参、park）      |
|     | TIMED_WAITING | 计时等待（sleep、wait(ms)、join(ms)） |
|     | TERMINATED    | 线程已结束                         |

## 3. 线程常用方法

|     | 方法                | 说明                     |
| --- | ----------------- | ---------------------- |
|     | `start()`         | 启动线程（只能调用一次）           |
|     | `run()`           | 线程执行的任务（不直接调用）         |
|     | `sleep(long ms)`  | 静态方法，当前线程休眠（不释放锁）      |
|     | `join()`          | 等待该线程执行完毕（底层是 wait）    |
|     | `yield()`         | 静态方法，让出 CPU 时间片（不一定生效） |
|     | `interrupt()`     | 中断线程（设置中断标志位）          |
|     | `setDaemon(true)` | 设置为守护线程                |
|     | `getState()`      | 获取线程状态                 |

```java
// join 示例
Thread t1 = new Thread(() -> { /* 耗时任务 */ });
t1.start();
t1.join();  // 主线程等待 t1 执行完毕
// sleep 示例
Thread.sleep(1000);  // 休眠 1 秒，不释放锁
```

## 4. 线程同步（synchronized）

### 同步代码块
```java
synchronized(锁对象) {
    // 临界区代码
}
```

### 同步方法
```java
// 普通同步方法：锁是 this（当前对象）
public synchronized void method() { }

// 静态同步方法：锁是 类名.class
public static synchronized void method() { }
```

**锁的对象：**
- 非静态方法（同步代码块）：任意对象，通常用 `this`
- 静态方法：`类名.class`

```java
// 互斥锁示例
class TicketSeller {
    private int tickets = 100;
    private final Object lock = new Object();

    public void sell() {
        synchronized (lock) {
            if (tickets > 0) {
                System.out.println(Thread.currentThread().getName() 
                    + " 卖了第 " + (tickets--) + " 张票");
            }
        }
    }
}
```

## 5. Lock 锁（java.util.concurrent.locks）

```java
class Counter {
    private int count = 0;
    private final Lock lock = new ReentrantLock();

    public void increment() {
        lock.lock();
        try {
            count++;
        } finally {
            lock.unlock();  // 必须在 finally 中释放
        }
    }
}
```

### synchronized vs Lock

|     | 对比项   | synchronized      | Lock              |
| --- | ----- | ----------------- | ----------------- |
|     | 实现    | JVM 层面（关键字）       | JDK 层面（接口）        |
|     | 释放锁   | 自动（代码块执行完/异常）     | 手动（必须 unlock）     |
|     | 尝试获取锁 | 阻塞，无法中断           | `tryLock()` 可非阻塞  |
|     | 公平锁   | 非公平               | 可选公平/非公平          |
|     | 精确唤醒  | 只能 notifyAll      | `Condition` 可精确唤醒 |
|     | 性能    | JDK 1.6 后优化，低竞争时优 | 高竞争时优             |

```java
// tryLock 示例
if (lock.tryLock(1, TimeUnit.SECONDS)) {
    try {
        // 处理
    } finally {
        lock.unlock();
    }
} else {
    System.out.println("获取锁超时，执行替代逻辑");
}
```

## 6. 线程间通信

### wait / notify / notifyAll（必须在 synchronized 内使用）

```java
class ProducerConsumer {
    private final Object lock = new Object();
    private boolean flag = false;

    // 生产者
    public void produce() throws InterruptedException {
        synchronized (lock) {
            while (flag) lock.wait();  // 已有产品，等待（while 防虚假唤醒）
            // 生产...
            flag = true;
            lock.notifyAll();          // 唤醒所有等待线程
        }
    }

    // 消费者
    public void consume() throws InterruptedException {
        synchronized (lock) {
            while (!flag) lock.wait(); // 没有产品，等待
            // 消费...
            flag = false;
            lock.notifyAll();
        }
    }
}
```

### Condition（配合 Lock 使用，更灵活）

```java
Lock lock = new ReentrantLock();
Condition condition = lock.newCondition();

// 等待
lock.lock();
try {
    while (条件不满足) condition.await();
    // 执行业务
} finally {
    lock.unlock();
}

// 唤醒
lock.lock();
try {
    修改条件;
    condition.signal();    // 唤醒一个
    // condition.signalAll();  // 唤醒所有
} finally {
    lock.unlock();
}
```

## 7. 线程池（ExecutorService）

推荐使用线程池管理线程，避免频繁创建销毁的开销。

```java
// 方式一：Executors 工具类（生产不推荐，OOM 风险）
ExecutorService pool1 = Executors.newFixedThreadPool(5);      // 固定大小
ExecutorService pool2 = Executors.newCachedThreadPool();       // 可缓存
ExecutorService pool3 = Executors.newSingleThreadExecutor();   // 单线程

// 方式二：ThreadPoolExecutor 手动创建（推荐）
ThreadPoolExecutor executor = new ThreadPoolExecutor(
    2,              // corePoolSize：核心线程数
    5,              // maximumPoolSize：最大线程数
    60,             // keepAliveTime：空闲线程存活时间
    TimeUnit.SECONDS,
    new LinkedBlockingQueue<>(10),  // 任务队列
    Executors.defaultThreadFactory(),
    new ThreadPoolExecutor.CallerRunsPolicy()  // 拒绝策略
);

// 提交任务
executor.execute(() -> System.out.println("Runnable 任务"));
Future<String> future = executor.submit(() -> "Callable 返回值");
String result = future.get();  // 获取返回值

// 关闭线程池
executor.shutdown();     // 等待任务执行完后关闭
// executor.shutdownNow(); // 立即关闭，尝试中断正在执行的任务
```

### 四种拒绝策略

| 策略 | 说明 |
|------|------|
| AbortPolicy（默认） | 抛 RejectedExecutionException |
| CallerRunsPolicy | 由提交任务的线程自己执行 |
| DiscardPolicy | 直接丢弃任务 |
| DiscardOldestPolicy | 丢弃队列中最老的任务 |

### 线程参数设置

- **CPU 密集型**：`corePoolSize = CPU 核心数 + 1`
- **IO 密集型**：`corePoolSize = CPU 核心数 * 2`（或 `CPU核心数 / (1 - 阻塞系数)`，阻塞系数约 0.8~0.9）

## 8. volatile 关键字

**两大特性**：**可见性**和**禁止指令重排**（没有原子性）。

```java
class FlagExample {
    private volatile boolean running = true;

    public void stop() {
        running = false;  // 立即对其它线程可见
    }

    public void work() {
        while (running) {
            // 没有 volatile，此线程可能永远看不到 running 的变化
        }
    }
}
```

### volatile vs synchronized

|     | 对比项  | volatile    | synchronized |
| --- | ---- | ----------- | ------------ |
|     | 原子性  | ❌ 不保证       | ✅ 保证         |
|     | 可见性  | ✅ 保证        | ✅ 保证         |
|     | 有序性  | ✅ 禁止指令重排    | ✅ 保证         |
|     | 性能   | 较优          | 较重           |
|     | 适用场景 | 状态标志、DCL 单例 | 需要原子操作的临界区   |

## 9. ThreadLocal

为每个线程提供独立的变量副本，线程间隔离，常用于数据库连接、Session 管理。

```java
private static ThreadLocal<String> threadLocal = new ThreadLocal<>();

// 存储
threadLocal.set("value");

// 获取
String value = threadLocal.get();

// 必须清理，防止内存泄漏！
threadLocal.remove();

// 带初始值
ThreadLocal<Integer> tl = ThreadLocal.withInitial(() -> 0);
```

## 10. 死锁

多个线程互相等待对方持有的锁，导致永远阻塞。

```java
// 死锁示例（两个线程死锁）
class DeadlockDemo {
    private final Object lock1 = new Object();
    private final Object lock2 = new Object();

    void method1() {
        synchronized (lock1) {
            synchronized (lock2) { /* 业务 */ }
        }
    }

    void method2() {
        synchronized (lock2) {
            synchronized (lock1) { /* 业务 */ }
        }
    }
}
```

**死锁四条件（全部满足才死锁）**：
1. **互斥**：资源只能被一个线程持有
2. **持有并等待**：持有锁的同时等待其他锁
3. **不可抢占**：已获取的锁不能被强制释放
4. **循环等待**：存在线程→资源的循环依赖链

**排查死锁**：`jstack <pid>` 可以检测死锁。

## 11. 线程安全集合（JUC）

这些类在高并发场景下比 `synchronized` 包装类性能更好：

|     | 类                                                     | 线程安全机制                    | 替代方案对比                         |
| --- | ----------------------------------------------------- | ------------------------- | ------------------------------ |
|     | ConcurrentHashMap                                     | CAS + synchronized（细粒度锁）  | Hashtable（全表锁）、synchronizedMap |
|     | CopyOnWriteArrayList                                  | 写时复制（读多写少）                | Vector、synchronizedList        |
|     | CopyOnWriteArraySet                                   | 基于 CopyOnWriteArrayList   | synchronizedSet                |
|     | ConcurrentLinkedQueue                                 | CAS 无锁算法                  | —                              |
|     | BlockingQueue（ArrayBlockingQueue/LinkedBlockingQueue） | ReentrantLock + Condition | 生产者-消费者专用                      |

```java
// ConcurrentHashMap 使用（推荐替代 HashMap + 外部同步）
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
map.put("key", 1);

// 原子操作
map.putIfAbsent("key", 2);  // key 不存在才放入
map.computeIfPresent("key", (k, v) -> v + 1);  // 存在则计算
```

> 📖 更多 JUC 并发工具（原子类、同步工具类等）见 [[java高级#9. JUC 并发工具|java高级 → JUC 并发工具]]。

# 14.IO流原理
以java程序为参照物：
1. 输入流：读取外部数据到程序（内存）中
2. 输出流：将程序（内存）中的数据输出到磁盘光盘中

## 1.流的分类
- 操作数据单位不同：字节流（8bit），字符流（按字符，对应几个字节）==字符流会自动进行编码解码（UTF-8，GBK）==
- 数据流的流向不同：输入流、输出流
- 流的角色不同：节点流、处理流/包装流

|     | 抽象基类 | 字节流          | 字符流    |
| --- | ---- | ------------ | ------ |
|     | 输入流  | InputStream  | Reader |
|     | 输出流  | OutputStream | Writer |

## 2. File 类（文件操作）

`java.io.File` 用于表示文件和目录路径名，**不涉及文件内容读写**。

```java
File file = new File("D:/example/test.txt");   // Windows
File dir = new File("docs");                     // 相对路径

// 基本操作
file.exists();              // 文件是否存在
file.isFile();              // 是否是文件
file.isDirectory();         // 是否是目录
file.length();              // 文件大小（字节）
file.getName();             // 文件名 test.txt
file.getPath();             // 路径（构造时传的）
file.getAbsolutePath();     // 绝对路径，补全为**绝对路径**，但保留 `.`（当前目录）、`..`（上级目录）、软链接 / 符号链接原样。
file.getCanonicalPath()     //绝对路径 + 化简 . /.. + 解析软链接 + 统一大小写（Windows），路径唯一
file.getParent();           // 父目录

// 创建 & 删除
file.createNewFile();       // 创建新文件，返回 boolean
dir.mkdir();                // 创建单级目录
dir.mkdirs();               // 创建多级目录（如 a/b/c）
file.delete();              // 删除文件或空目录

// 目录遍历
File[] files = dir.listFiles();                  // 列出所有子文件/目录
String[] names = dir.list();                     // 只返回名称
File[] txtFiles = dir.listFiles(f -> f.getName().endsWith(".txt"));
```

**常见陷阱**：File 删除的文件不会进回收站；File 操作不涉及内容读写。

## 3. 字节流（InputStream / OutputStream）

适合操作**所有类型文件**（图片、视频、压缩包等）。

### 3.1 FileInputStream —— 文件字节输入流

```java
// 方式一：构造器传入 File 对象
File file = new File("input.txt");
FileInputStream fis = new FileInputStream(file);

// 方式二：构造器传入路径字符串
FileInputStream fis = new FileInputStream("input.txt");

// 读取方式一：单字节读取（不推荐，效率低）
int data;
while ((data = fis.read()) != -1) {     // read() 返回 int（0~255），-1 表示读完
    System.out.print((char) data);
}

// 读取方式二：批量读取（推荐，效率高）
byte[] buffer = new byte[1024];
int len;
while ((len = fis.read(buffer)) != -1) {
    // 读取到 buffer 中，返回实际读取字节数 len
    System.out.print(new String(buffer, 0, len));
}

fis.close();  // 必须关闭释放资源
```

### 3.2 FileOutputStream —— 文件字节输出流

```java
FileOutputStream fos = new FileOutputStream("output.txt");//new FileOutputStream("output.txt" ，true)表示追加，不加true是覆盖
// 追加模式：new FileOutputStream("output.txt", true);

String content = "Hello, Java IO!";
fos.write(content.getBytes());              // 写入全部字节
fos.write(content.getBytes(), 0, 5);        // 写入部分字节，第二个参数表示起始位置，最后一个参数表示一共传入字符串的长度

fos.flush();  // 刷新缓冲区（字节流 flush 为空实现，字符流必须）
fos.close();
```

### 3.3 完整拷贝文件示例

```java
public static void copyFile(String src, String dest) throws IOException {
    try (FileInputStream fis = new FileInputStream(src);
         FileOutputStream fos = new FileOutputStream(dest)) {

        byte[] buffer = new byte[8192];  // 8KB 缓冲区
        int len;
        while ((len = fis.read(buffer)) != -1) {
            fos.write(buffer, 0, len);
        }
    }  // 自动 close（try-with-resources）
}
```

## 4. 字符流（Reader / Writer）

适合操作**纯文本文件**（.txt、.java、.xml、.json 等），直接处理字符，自动处理编码。

### 4.1 FileReader —— 文件字符输入流

```java
// 读取方式一：单字符读取
FileReader fr = new FileReader("test.txt");
int ch;
while ((ch = fr.read()) != -1) {
    System.out.print((char) ch);
}
fr.close();

// 读取方式二：批量读取（推荐）
FileReader fr = new FileReader("test.txt");
char[] buffer = new char[1024];
int len;
while ((len = fr.read(buffer)) != -1) {
    System.out.print(new String(buffer, 0, len));
}
fr.close();
```

### 4.2 FileWriter —— 文件字符输出流

```java
FileWriter fw = new FileWriter("test.txt");          // 覆盖模式
// FileWriter fw = new FileWriter("test.txt", true); // 追加模式

fw.write("Hello, 你好！");
fw.write("\r\n");                   // 换行（Windows）
fw.write("第二行");
fw.flush();  // 必须 flush 或 close，否则数据可能未写入文件
fw.close();
```

### 字节流 vs 字符流选择

|     |              场景              |                     推荐                      |
| :-: | :--------------------------: | :-----------------------------------------: |
|     |         图片、视频、音频、压缩包         | **字节流**（FileInputStream / FileOutputStream） |
|     | 纯文本文件（.txt、.java、.xml、.json） |      **字符流**（FileReader / FileWriter）       |
|     |             不确定              |            **字节流**（字节流可以处理任何文件）             |

### 节点流 vs 处理流
- 节点流：从特定数据源读写数据
- 处理流：也叫包装流，连接在已存在的流上，为程序提供更为强大的读写功能
![[节点流vs处理流.png]]
## 5. 缓冲流（Buffered）—— 性能提升

**装饰器模式**：包装已有流，提供缓冲区，显著提升 I/O 性能。

|     |        字节缓冲流         |     字符缓冲流      |
| :-: | :------------------: | :------------: |
|     | BufferedInputStream  | BufferedReader |
|     | BufferedOutputStream | BufferedWriter |

```java
// 字节缓冲流（默认缓冲区 8192 字节 = 8KB）
BufferedInputStream bis = new BufferedInputStream(new FileInputStream("input.txt"));
BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("output.txt"));

byte[] buffer = new byte[8192];
int len;
while ((len = bis.read(buffer)) != -1) {
    bos.write(buffer, 0, len);
}
bos.flush();  // 确保缓冲区数据全部写出
bis.close();
bos.close();


// 字符缓冲流 —— 特有方法：readLine() / newLine()
BufferedReader br = new BufferedReader(new FileReader("input.txt"));
BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"));

String line;
while ((line = br.readLine()) != null) {     // 一次读一行（不含换行符）
										//这里要注意，读取完会返回null
    bw.write(line);
    bw.newLine();                            // 跨平台换行
}
br.close();
bw.close();
```

**缓冲流速度对比**（经验数据）：

|     |             读取方式              |   耗时（相对）   |
| :-: | :---------------------------: | :--------: |
|     |      单字节 FileInputStream      | 最慢，约 100x  |
|     | 批量 byte[8192] FileInputStream |     中等     |
|     |   BufferedInputStream + 单字节   |     较慢     |
|     |   BufferedInputStream + 批量    | **最快（推荐）** |

## 6. 转换流（InputStreamReader / OutputStreamWriter）

**作用**：字节流 ↔ 字符流的桥梁，可**指定字符编码**。

```java
// InputStreamReader：字节输入流 → 字符输入流
FileInputStream fis = new FileInputStream("test.txt");
InputStreamReader isr = new InputStreamReader(fis, "UTF-8");  // 指定编码
BufferedReader br = new BufferedReader(isr);
String line;
while ((line = br.readLine()) != null) {
    System.out.println(line);
}
br.close();

// OutputStreamWriter：字符输出流 → 字节输出流
FileOutputStream fos = new FileOutputStream("test.txt");
OutputStreamWriter osw = new OutputStreamWriter(fos, "UTF-8");
BufferedWriter bw = new BufferedWriter(osw);
bw.write("你好，世界！");
bw.close();

// 常见编码读取
new InputStreamReader(fis, "UTF-8");
new InputStreamReader(fis, "GBK");
new InputStreamReader(fis, StandardCharsets.UTF_8);  // Java 7+ 推荐
```

## 7. 对象流 / 序列化（ObjectInputStream / ObjectOutputStream）

将 Java 对象写入文件或从文件读取 Java 对象。

### 要求
- 类必须实现 `Serializable` 接口（标记接口，无需实现方法）或者 `Externalizable`接口（该接口有方法需要实现），一般用 `Serializable` 接口
- 类需指定 `serialVersionUID`（版本控制）

```java
// 实体类
class User implements Serializable {
    private static final long serialVersionUID = 1L;  // 版本号，反序列化校验用

    private Long id;
    private String name;
    private transient String password;  // transient 修饰的字段不会被序列化

    // getter/setter...
}

// 序列化：对象 → 文件
User user = new User(1L, "小明", "123456");

try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("user.dat"))) {
    oos.writeObject(user);
    System.out.println("对象已序列化");
}

// 反序列化：文件 → 对象
try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("user.dat"))) {
    User deserialized = (User) ois.readObject();
    System.out.println(deserialized.getName());  // 小明
    System.out.println(deserialized.getPassword());  // null（transient 字段）
}
```

### 序列化注意事项
- 序列化就是保存数据时也保存数据的值和类型，即`ObjectOutputStream`
- 反序列化就是恢复数据时恢复数据的值和类型，即`ObjectInputStream

1. 读取（反序列化）的顺序和保存数据（序列化）的顺序需要一致
2. 实现序列化或者反序列化对象，需要实现 `Serializable` 接口（标记接口，无需实现方法）
3. 序列化的类中需要添加serialVersionUID 版本号，反序列化校验用，提高版本兼容性
4. 序列化对象时，默认将里面的所有属性进行序列化，但除了static或transient修饰的成员
5. 序列化对象时，要求里面属性的类型也需要是实现序列化接口
6. 序列化具有可继承性，如果某类已经实现了序列化，则他所有子类默认实现序列化

|     |         要点         | 说明                                         |
| :-: | :----------------: | :----------------------------------------- |
|     |    `transient`     | 修饰的字段不参与序列化，反序列化后为默认值                      |
|     | `serialVersionUID` | 若不指定，JVM 会根据类结构自动生成；类结构改变后 UID 变化，反序列化会失败  |
|     |        静态变量        | 不属于对象，不会被序列化                               |
|     |       父类序列化        | 父类未实现 Serializable，父类字段不会被序列化              |
|     |       集合序列化        | `ArrayList`、`HashMap` 等集合类已实现 Serializable |


## 8. 数据流（DataInputStream / DataOutputStream）

按 Java 基本数据类型读写文件（读写跨平台）。

```java
// 写入
try (DataOutputStream dos = new DataOutputStream(new FileOutputStream("data.bin"))) {
    dos.writeInt(100);
    dos.writeDouble(3.14);
    dos.writeUTF("你好");       // UTF-8 编码的字符串
    dos.writeBoolean(true);
}

// 读取（必须与写入顺序一致）
try (DataInputStream dis = new DataInputStream(new FileInputStream("data.bin"))) {
    int i = dis.readInt();        // 100
    double d = dis.readDouble();  // 3.14
    String s = dis.readUTF();     // 你好
    boolean b = dis.readBoolean();// true
}
```

## 9. 打印流（PrintStream / PrintWriter）

方便地输出各种数据类型，**不会抛出 IOException**。

```java
// PrintStream：字节打印流（System.out 就是 PrintStream）
PrintStream ps = new PrintStream(new FileOutputStream("log.txt"));
ps.println("这是日志信息");
ps.printf("姓名：%s，年龄：%d%n", "小明", 18);
ps.close();

// PrintWriter：字符打印流（推荐文本输出）
PrintWriter pw = new PrintWriter(new FileWriter("log.txt"), true);  // autoFlush
pw.println("第一行");
pw.printf("数值：%.2f", 3.14159);
pw.close();

// 重定向标准输出
System.setOut(new PrintStream("output.txt"));
System.out.println("这条输出会写入文件而不是控制台");
```

## 10. 标准输入输出（System.in / System.out / System.err）
System.in 编译类型 InputStream
               运行类型 BufferInputStream

System.out 编译类型 PrintStream
               运行类型 PrintStream
```java
// 标准输入（键盘输入）
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
System.out.print("请输入姓名：");
String name = br.readLine();                       // 读取一行

// 简化版：Scanner
Scanner scanner = new Scanner(System.in);
String name2 = scanner.nextLine();
int age = scanner.nextInt();

// 标准输出（控制台打印）
System.out.println("普通输出");       // PrintStream
System.err.println("错误输出");       // PrintStream，红色字体

// 标准输入重定向
System.setIn(new FileInputStream("input.txt"));
Scanner sc = new Scanner(System.in);
while (sc.hasNextLine()) {
    System.out.println(sc.nextLine());
}
```

## 11. try-with-resources（自动关闭资源）

Java 7 引入，自动调用 `Closeable` 资源的 `close()` 方法，**无需手动 close**。

```java
// ❌ 传统写法（Java 7 之前）
FileInputStream fis = null;
try {
    fis = new FileInputStream("test.txt");
    // 读取操作...
} catch (IOException e) {
    e.printStackTrace();
} finally {
    if (fis != null) {
        try { fis.close(); } catch (IOException e) { }
    }
}

// ✅ try-with-resources（推荐，Java 7+）
try (FileInputStream fis = new FileInputStream("test.txt");
     FileOutputStream fos = new FileOutputStream("out.txt")) {

    byte[] buffer = new byte[8192];
    int len;
    while ((len = fis.read(buffer)) != -1) {
        fos.write(buffer, 0, len);
    }
}  // 自动调用 fis.close() 和 fos.close()，即使发生异常

// 可关闭多个资源，按声明顺序的逆序关闭
try (BufferedReader br = new BufferedReader(new FileReader("a.txt"));
     BufferedWriter bw = new BufferedWriter(new FileWriter("b.txt"))) {
    // 处理...
}
```

**原理**：`try()` 中的资源必须实现 `AutoCloseable` 或 `Closeable` 接口。所有 IO 流类都实现了该接口。

> 📖 Java 9 对 try-with-resources 的增强（可使用 effectively final 变量）见 [[java高级#12. 私有接口方法 try-with-resources 增强（Java 9）|java高级 → try-with-resources 增强]]。

## 12. 随机访问流（RandomAccessFile）

可直接跳转到文件的任意位置读写，**不属于 InputStream/OutputStream 体系**。

```java
// 模式：
// "r"   — 只读
// "rw"  — 读写
// "rws" — 读写 + 同步写入文件+元数据
// "rwd" — 读写 + 同步写入文件数据
RandomAccessFile raf = new RandomAccessFile("test.txt", "rw");

// 获取 & 设置文件指针位置
long pos = raf.getFilePointer();   // 当前指针位置
raf.seek(100);                     // 跳转到第 100 字节处

// 读写（类似 DataInputStream/DataOutputStream）
raf.writeInt(123);
raf.writeUTF("Hello");
raf.seek(0);                       // 回到文件开头
int i = raf.readInt();

// 获取文件长度（常用于断点续传）
long length = raf.length();

raf.close();

// 断点续传示意
long savedPosition = getSavedPosition();  // 从数据库或文件读取已传位置
raf.seek(savedPosition);                  // 跳转到断点处继续
byte[] buffer = new byte[4096];
int len;
while ((len = raf.read(buffer)) != -1) {
    // 上传...
    savePosition(raf.getFilePointer());   // 记录当前位置
}
```

## 13. NIO 基础（Java 7+ java.nio.file）

JDK 7 引入 `java.nio.file` 包，比 `java.io.File` 更强大、更易用。

### 使用 Files / Paths（替代 File 类）

```java
Path path = Paths.get("D:", "docs", "test.txt");      // D:\docs\test.txt
Path path2 = Paths.get("test.txt");                     // 相对路径

// 文件操作
Files.exists(path);
Files.isRegularFile(path);
Files.isDirectory(path);
Files.size(path);                  // 文件大小
Files.getLastModifiedTime(path);   // 最后修改时间

// 创建 & 删除
Files.createFile(path);                            // 创建文件
Files.createDirectories(Paths.get("a/b/c"));       // 创建多级目录
Files.delete(path);                                // 删除（文件不存在抛异常）
Files.deleteIfExists(path);                        // 安全删除

// 复制 & 移动
Files.copy(source, target, StandardCopyOption.REPLACE_EXISTING);
Files.move(source, target);

// 文件属性
Files.getAttribute(path, "size");
Files.getAttribute(path, "creationTime");
Files.getAttribute(path, "lastModifiedTime");

// 读取文件所有行（适合小文件）
List<String> lines = Files.readAllLines(path, StandardCharsets.UTF_8);

// 写入文件
Files.write(path, "Hello, NIO!".getBytes());
Files.write(path, lines, StandardCharsets.UTF_8);

// 遍历目录
try (Stream<Path> stream = Files.walk(Paths.get("src"))) {
    stream.filter(p -> p.toString().endsWith(".java"))
          .forEach(System.out::println);
}
```

### NIO 核心概念

| 概念 | 说明 |
|:----:|:----|
| **Channel（通道）** | 双向读写，如 `FileChannel`、`SocketChannel` |
| **Buffer（缓冲区）** | 数据的容器，如 `ByteBuffer`、`CharBuffer` |
| **Selector（选择器）** | 单个线程管理多个 Channel（网络编程） |

```java
// FileChannel 快速拷贝
try (FileChannel in = FileChannel.open(Paths.get("src.zip"), StandardOpenOption.READ);
     FileChannel out = FileChannel.open(Paths.get("dest.zip"),
             StandardOpenOption.CREATE, StandardOpenOption.WRITE)) {

    in.transferTo(0, in.size(), out);  // 零拷贝，效率极高
}
```

## 14. 常用 IO 模式总结

### 装饰器模式（IO 流的设计模式）

```java
// 核心：一层套一层，增强功能
BufferedReader br = new BufferedReader(
    new InputStreamReader(
        new FileInputStream("test.txt"), "UTF-8"
    )
);
// FileInputStream：底层读取字节
// InputStreamReader：字节 → 字符 + 指定编码
// BufferedReader：提供缓冲 + readLine()
```

### IO 流速查表

|     |      使用场景      | 推荐组合                                                                  |
| :-: | :------------: | :-------------------------------------------------------------------- |
|     | 复制二进制文件（图片/视频） | `FileInputStream` + `FileOutputStream` + `byte[8192]`                 |
|     |  复制二进制文件（最优）   | `BufferedInputStream` + `BufferedOutputStream`                        |
|     |   读文本文件（按行）    | `BufferedReader` + `FileReader`                                       |
|     |     写文本文件      | `BufferedWriter` + `FileWriter`                                       |
|     |   读文本（指定编码）    | `BufferedReader` + `InputStreamReader(UTF-8)` + `FileInputStream`     |
|     |   Java 对象持久化   | `ObjectOutputStream` / `ObjectInputStream`                            |
|     |   随机访问/断点续传    | `RandomAccessFile`                                                    |
|     |      键盘输入      | `Scanner(System.in)` 或 `BufferedReader(InputStreamReader(System.in))` |
|     |    控制台格式化输出    | `System.out`(PrintStream) / `System.err`                              |
|     |  大文件快速处理（NIO）  | `Files.readAllLines()` / `Files.walk()` / `FileChannel`               |


# 15. 反射（Reflection）

Java 反射机制是指在**运行状态**中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意方法和属性。这种动态获取信息以及动态调用对象方法的功能称为 Java 的反射机制。
在反射中，可以把方法视为对象（万物皆对象）

## 反射机制示意图
![[反射机制示意图.png]]
## 1. 反射的核心类

|     |       类       |       用途       |                          获取方式                          |
| :-: | :-----------: | :------------: | :----------------------------------------------------: |
|     |    `Class`    | 代表一个类，获取类的完整信息 | `类名.class` / `对象.getClass()` / `Class.forName("全限定名")` |
|     | `Constructor` |    代表类的构造方法    |           `clazz.getDeclaredConstructors()`            |
|     |   `Method`    |     代表类的方法     |              `clazz.getDeclaredMethods()`              |
|     |    `Field`    |   代表类的属性/字段    |              `clazz.getDeclaredFields()`               |
|     |  `Parameter`  |     代表方法参数     |                `method.getParameters()`                |
|     | `Annotation`  |      代表注解      |            `clazz.getDeclaredAnnotations()`            |

## 2. 获取 Class 对象的三种方式

```java
// 方式一：Class.forName() —— 最常用（编译期未知类名时）
Class<?> clazz1 = Class.forName("com.example.User");

// 方式二：类名.class —— 最安全（编译期已知类）
Class<User> clazz2 = User.class;

// 方式三：对象.getClass() —— 已有对象时
User user = new User();
Class<?> clazz3 = user.getClass();

// 三种方式获取的是同一个 Class 对象（同一个类在 JVM 中只有一份字节码）
System.out.println(clazz1 == clazz2);  // true
System.out.println(clazz2 == clazz3);  // true
```

## 3. 操作构造方法（Constructor）

```java
Class<User> clazz = User.class;

// 获取所有构造方法（包括 private）
Constructor<?>[] constructors = clazz.getDeclaredConstructors();

// 获取无参构造并创建对象
User user1 = clazz.getDeclaredConstructor().newInstance();  // 等效于 new User()

// 获取有参构造并创建对象
Constructor<User> constructor = clazz.getDeclaredConstructor(String.class, int.class);
User user2 = constructor.newInstance("小明", 18);

// 调用私有构造方法
Constructor<User> privateCon = clazz.getDeclaredConstructor(String.class);
privateCon.setAccessible(true);  // 暴力反射：解除 private 限制
User user3 = privateCon.newInstance("秘密创建");
```

## 4. 操作方法（Method）

```java
Class<?> clazz = Class.forName("com.example.User");
Object obj = clazz.getDeclaredConstructor().newInstance();

// 获取所有 public 方法（含继承的）
Method[] methods = clazz.getMethods();

// 获取本类所有方法（含 private，不含继承）
Method[] declaredMethods = clazz.getDeclaredMethods();

// 调用 public 方法
Method setName = clazz.getMethod("setName", String.class);
setName.invoke(obj, "小明");

// 调用 private 方法
Method privateMethod = clazz.getDeclaredMethod("hiddenMethod");
privateMethod.setAccessible(true);
privateMethod.invoke(obj);

// 调用静态方法
Method staticMethod = clazz.getMethod("staticMethod");
staticMethod.invoke(null);  // 静态方法，对象传 null

// 获取方法返回值类型
Class<?> returnType = setName.getReturnType();

// 获取方法参数类型
Class<?>[] paramTypes = setName.getParameterTypes();
```

## 5. 操作属性（Field）

```java
Class<?> clazz = Class.forName("com.example.User");
Object obj = clazz.getDeclaredConstructor().newInstance();

// 获取所有 public 字段（含继承的）
Field[] fields = clazz.getFields();

// 获取本类所有字段（含 private）
Field[] declaredFields = clazz.getDeclaredFields();

// 获取指定字段
Field nameField = clazz.getDeclaredField("name");
nameField.setAccessible(true);              // 访问 private 字段必须

// 读写字段
nameField.set(obj, "小明");                  // 设置值
String value = (String) nameField.get(obj); // 获取值

// 获取字段类型
Class<?> fieldType = nameField.getType();    // String.class

// 读写静态字段
Field staticField = clazz.getDeclaredField("STATIC_VALUE");
staticField.setAccessible(true);
Object staticVal = staticField.get(null);   // 静态字段，对象传 null
```

## 6. 操作注解（Annotation）

```java
Class<?> clazz = Class.forName("com.example.User");

// 获取类上的注解
Annotation[] annotations = clazz.getDeclaredAnnotations();

// 获取指定的注解
TableName tableName = clazz.getAnnotation(TableName.class);
String table = tableName.value();

// 获取字段上的注解（ORM 框架常用）
Field[] fields = clazz.getDeclaredFields();
for (Field field : fields) {
    Column column = field.getAnnotation(Column.class);
    if (column != null) {
        String columnName = column.name();
        boolean isPrimaryKey = column.isPrimaryKey();
    }
}
```

## 7. 动态代理（反射的经典应用）

```java
// 定义接口
interface UserService {
    void addUser(String name);
    void deleteUser(int id);
}

// 目标对象
class UserServiceImpl implements UserService {
    @Override
    public void addUser(String name) {
        System.out.println("添加用户：" + name);
    }
    @Override
    public void deleteUser(int id) {
        System.out.println("删除用户：" + id);
    }
}

// 动态代理
class LogProxy implements InvocationHandler {
    private final Object target;

    public LogProxy(Object target) {
        this.target = target;
    }

    @SuppressWarnings("unchecked")
    public static <T> T createProxy(T target) {
        return (T) Proxy.newProxyInstance(
            target.getClass().getClassLoader(),
            target.getClass().getInterfaces(),
            new LogProxy(target)
        );
    }

    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("[日志] 调用方法：" + method.getName() + "，参数：" + Arrays.toString(args));
        Object result = method.invoke(target, args);  // 反射调用目标方法
        System.out.println("[日志] 方法执行完毕：" + method.getName());
        return result;
    }
}

// 使用示例
UserService userService = new UserServiceImpl();
UserService proxy = LogProxy.createProxy(userService);
proxy.addUser("小明");
```

## 8. 获取泛型信息

```java
// 在运行时获取泛型实参（框架中常用）
abstract class BaseDao<T> {
    public Class<T> getEntityClass() {
        // 获取当前类（子类）的父类的泛型信息
        ParameterizedType type = (ParameterizedType) this.getClass().getGenericSuperclass();
        Type[] typeArgs = type.getActualTypeArguments();
        return (Class<T>) typeArgs[0];  // 第一个泛型参数
    }
}

class UserDao extends BaseDao<User> { }

// 使用
UserDao dao = new UserDao();
Class<User> entityClass = dao.getEntityClass();  // User.class

// 获取方法参数的泛型
Method method = clazz.getMethod("findList", List.class);
Type[] genericParamTypes = method.getGenericParameterTypes();
for (Type type : genericParamTypes) {
    if (type instanceof ParameterizedType) {
        ParameterizedType pt = (ParameterizedType) type;
        Type[] actualTypes = pt.getActualTypeArguments();
        // 例如：List<User>  ->  获取到 User
    }
}
```

## 9. 操作数组（Array 类）

```java
import java.lang.reflect.Array;

// 动态创建数组
int[] intArray = (int[]) Array.newInstance(int.class, 5);
String[] strArray = (String[]) Array.newInstance(String.class, 3);

// 动态读写数组元素
Array.set(intArray, 0, 100);
int value = Array.getInt(intArray, 0);  // 100

Array.set(strArray, 0, "Hello");
String str = (String) Array.get(strArray, 0);

// 获取数组长度和类型
int length = Array.getLength(intArray);
Class<?> componentType = intArray.getClass().getComponentType();  // int.class
```

## 10. 反射的应用场景

|     |      场景      | 说明                   |           代表框架            |
| :-: | :----------: | :------------------- | :-----------------------: |
|     |   **框架核心**   | 通过配置文件或注解动态创建对象、注入依赖 |        Spring IOC         |
|     |   **ORM**    | 根据类名/字段映射到数据库表和列     |        MyBatis、JPA        |
|     | **序列化/反序列化** | 将对象转为 JSON/XML 或反向   |       Jackson、Gson        |
|     |   **动态代理**   | 在运行时生成代理对象，增强方法      | Spring AOP、MyBatis Mapper |
|     |  **IDE 工具**  | 代码补全、自动提示、查看类结构      |       IntelliJ IDEA       |
|     |   **测试框架**   | 通过反射扫描 @Test 注解并执行方法 |       JUnit、TestNG        |

## 11. 反射的优缺点

|     |         优点          |                          缺点                           |
| :-: | :-----------------: | :---------------------------------------------------: |
|     | 运行期动态操作类 —— 提高代码灵活性 |            **性能开销**：比直接调用慢（方法调用绕过 JIT 优化）             |
|     |      框架开发的核心技术      | **安全限制**：`setAccessible(true)` 可能被 SecurityManager 禁止 |
|     |    破解封装性，实现通用操作     |                 **代码可读性差**：相比直接调用更复杂                  |
|     |    泛型擦除后仍可获取原始类型    |                 **运行时错误风险**：编译期不能发现异常                 |

### 性能优化建议

```java
// 不推荐：每次调用都反射获取方法
for (int i = 0; i < 10000; i++) {
    Method m = clazz.getMethod("doSomething");
    m.invoke(obj);
}

// 推荐：缓存 Method 对象，避免反复查找
Method cachedMethod = clazz.getMethod("doSomething");
cachedMethod.setAccessible(true);
for (int i = 0; i < 10000; i++) {
    cachedMethod.invoke(obj);  // 复用 Method 对象
}
```

## 12. 完整示例：模拟简易 ORM

```java
import java.lang.annotation.*;
import java.lang.reflect.*;
import java.util.*;

// 自定义注解
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@interface Table {
    String value();
}

@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
@interface Column {
    String value();
    boolean isPrimaryKey() default false;
}

// 实体类
@Table("t_user")
class User {
    @Column(value = "id", isPrimaryKey = true)
    private Long id;
    @Column("user_name")
    private String name;
    @Column("user_age")
    private Integer age;

    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public Integer getAge() { return age; }
    public void setAge(Integer age) { this.age = age; }
}

// 简易 ORM 工具
class SimpleORM {
    public static String generateInsertSQL(Object obj) {
        Class<?> clazz = obj.getClass();
        Table table = clazz.getAnnotation(Table.class);
        if (table == null) throw new IllegalArgumentException("缺少 @Table 注解");

        String tableName = table.value();
        StringBuilder columns = new StringBuilder();
        StringBuilder values = new StringBuilder();

        Field[] fields = clazz.getDeclaredFields();
        for (Field field : fields) {
            field.setAccessible(true);
            Column col = field.getAnnotation(Column.class);
            if (col == null) continue;

            try {
                Object value = field.get(obj);
                if (value == null) continue;

                if (columns.length() > 0) columns.append(", ");
                if (values.length() > 0) values.append(", ");
                columns.append(col.value());
                values.append(value instanceof String ? "'" + value + "'" : value);
            } catch (IllegalAccessException e) {
                e.printStackTrace();
            }
        }

        return String.format("INSERT INTO %s (%s) VALUES (%s);", tableName, columns, values);
    }
}

// 使用
public class ORMDemo {
    public static void main(String[] args) {
        User user = new User();
        user.setId(1L);
        user.setName("小明");
        user.setAge(18);

        String sql = SimpleORM.generateInsertSQL(user);
        System.out.println(sql);
        // 输出：INSERT INTO t_user (id, user_name, age) VALUES (1, '小明', 18);
    }
}
```


# 16. Lambda 表达式（Java 8+）

Lambda 表达式允许把**函数作为方法的参数传递**，使代码更加简洁。

## 基本语法

```java
(参数列表) -> { 方法体 }

// 简写规则
(a, b) -> a + b           // 单行可省略 {} 和 return
a -> a * 2                 // 单参数可省略 ()
() -> System.out.println("Hello")  // 无参数
```

## 常见使用场景

```java
// 线程
new Thread(() -> System.out.println("Lambda")).start();
// 排序
list.sort((s1, s2) -> s1.compareTo(s2));
// 遍历
list.forEach(System.out::println);
```

> 📖 **完整进阶内容见 [[java高级#1. Lambda 表达式|java高级 → Lambda]]** 包括：函数式接口（四大内置函数式接口）、方法引用 `::`、变量捕获、Optional 类、Stream API、CompletableFuture 等。


# 17. Stream API（Java 8+）

Stream 是 Java 8 引入的函数式编程 API，用于对集合数据进行**声明式处理**（链式操作）。

## 快速概览

```java
// 常见操作链：创建 → 中间操作 → 终端操作
list.stream()                          // 1. 创建
    .filter(n -> n > 0)                // 2. 中间操作（过滤、映射、排序、去重...）
    .map(String::valueOf)              // 3. 终端操作（收集、聚合、遍历、匹配...）
    .collect(Collectors.toList());
```

**三大特点**：不存储数据、函数式编程、惰性求值（无终端操作时不执行）。

## 常用示例速查

```java
// 过滤 + 映射 + 收集
List<Integer> result = list.stream()
    .filter(s -> s.startsWith("a"))
    .map(String::length)
    .collect(Collectors.toList());

// 分组
Map<String, List<Person>> byCity = people.stream()
    .collect(Collectors.groupingBy(Person::getCity));

// 并行流（大数据量）
list.parallelStream().filter(...).count();
```

> 📖 **完整内容与详解见 [[java高级#5. Stream API|java高级 → Stream API]]** 包括：所有中间/终端操作详解、高级收集器（groupingBy/partitioningBy/summarizingInt）、并行流最佳实践、综合示例等。


# 关联笔记
> [!info] 关联笔记
> - [[java学习]] — 总笔记
> - [[java高级]] — Java 8 核心特性（Lambda、Stream、Optional、CompletableFuture 等）& Java 9~24 新特性精选