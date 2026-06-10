---
tags:
  - java基础
  - 笔记
aliases:
  - java学习
updated: 2026-06-10 16:04
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
  - [[java基础#(13)接口|接口]]（接口特性 / 抽象类与接口区别）
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
- [[java基础#Lombok|Lombok]]（@Slf4j / @Data / @NoArgsConstructor / @AllArgsConstructor）
- [[java基础#Spring   IOC：|Spring IOC]]（@Component / @Controller / @Service / @Repository / @Primary）
- [[java基础#编写controller|编写 Controller]]（@RequestMapping / @GetMapping / @PostMapping / 参数提取注解）

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



**注**：JDK 1.8 以后，接口里可以有静态方法和方法体了。

**注**：JDK 1.8 以后，接口允许包含具体实现的方法，该方法称为"默认方法"，默认方法使用 default 关键字修饰。更多内容可参考 [Java 8 默认方法](https://www.runoob.com/java/java8-default-methods.html)。

**注**：JDK 1.9 以后，允许将方法定义为 private，使得某些复用的代码不会把方法暴露出去。更多内容可参考 [Java 9 私有接口方法](https://www.runoob.com/java/java9-private-interface-methods.html)。



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

Java 8 引入 `java.time` 包，线程安全、不可变。

|     | 类                   | 说明          | 示例                                          |
| --- | ------------------- | ----------- | ------------------------------------------- |
|     | `LocalDate`         | 日期（不含时间）    | `LocalDate.now()`                           |
|     | `LocalTime`         | 时间（不含日期）    | `LocalTime.now()`                           |
|     | `LocalDateTime`     | 日期 + 时间     | `LocalDateTime.now()`                       |
|     | `Instant`           | 时间戳（UTC）    | `Instant.now()`                             |
|     | `Duration`          | 时间间隔（秒/纳秒）  | `Duration.between(t1, t2)`                  |
|     | `Period`            | 日期间隔（年/月/日） | `Period.between(d1, d2)`                    |
|     | `DateTimeFormatter` | 格式化/解析      | `DateTimeFormatter.ofPattern("yyyy-MM-dd")` |

```java
// 创建
LocalDateTime now = LocalDateTime.now();
LocalDateTime specific = LocalDateTime.of(2026, 6, 10, 14, 30);

// 格式化
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
String formatted = now.format(dtf);

// 字符串解析
LocalDateTime parsed = LocalDateTime.parse("2026-06-10 14:30:00", dtf);

// 日期运算（不可变，原对象不变，返回新对象）
LocalDateTime tomorrow = now.plusDays(1);
LocalDateTime lastMonth = now.minusMonths(1);
```

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

# 14.IO流原理
1. 输入流：读取外部数据到程序（内存）中
2. 输出流：将程序（内存）中的数据输出到磁盘光盘中

## 1.流的分类
- 操作数据单位不同：字节流（8bit），字符流（按字符，对应几个字节）
- 数据流的流向不同：输入流、输出流
- 流的角色不同：节点流、处理流/包装流

|     | 抽象基类 | 字节流          | 字符流    |
| --- | ---- | ------------ | ------ |
|     | 输入流  | InputStream  | Reader |
|     | 输出流  | OutputStream | Writer |

# Lombok
```java
@Slf4j  用于进行日志记录
    	log.info("这是一条日志");
        log.warn("WARN级别");
        log.error("ERROR级别");

/*
Lombok 提供的一个注解，用来在类中自动生成一个 SLF4J 的 logger 对象，命名通常为 log。
要点
作用：在类中自动生成一个私有的、静态最终的 Logger 字段，名称为 log，类型为 org.slf4j.Logger。
使用场景：简化在类中使用日志的代码，无需手动声明 Logger。
依赖：需要 Lombok 和一个实现 SLF4J 的日志实现（如 Logback、Log4j2 等
*/

```

```java
ObjectMapper objectMapper = new ObjectMapper(); //转换为json
//其输出为{"name":"小明","age":18}
```

```java
Person person = objectMapper.readValue(json, Person.class); // json转换回来
//其输出为Person(name=小明, age=18)
```

```java
@Data                   //getter setter
@NoArgsConstructor      //无参
@AllArgsConstructor     //全参
/*
Lombok 的注解:
@Data
为所有字段生成 getter/setter、toString、equals、hashCode、以及一个需要时的某些构造方法的组合，等价于 @Getter、@Setter、@ToString、@EqualsAndHashCode、@RequiredArgsConstructor 的组合。
使用场景：想要一个简单的数据载体类，字段较多时非常方便。

@NoArgsConstructor
作用：生成一个无参构造方法。
使用场景：需要一个无参构造，或框架（如 JPA、Jackson）要求。

@AllArgsConstructor
作用：生成一个包含所有字段的全参构造方法。
使用场景：快速创建对象，或在测试中需要完整字段初始化。
*/
```

# Spring   IOC：

```java
@Component
@Controller
@Service
@Repository
//都能实现Spring容器管理Bean
```

```java
@Primary//主要的，多个Bean时指定其中一个
```



# 编写controller

HTTP：

请求报文：

- 请求行：url里可以？后面表示信息
- 消息头：request.header提取出来
- 消息体：requestbody注解提取出来，json格式

响应报文：





```java
@RequestMapping("/api/v1")//能将方法的共有前缀与后面的进行拼接，就不用重复写
 @GetMapping("/hello")//表示接收的是get请求
 @PostMapping("/hello")//表示接收的是post请求
 @PutMapping("/hello")//表示接收的是put请求
```

```java
@RequestHeader//提取header参数
@PostMapping("/hello")
public String head1(@RequestHeader(required = false, defaultvalue = "默认值") String authorization){//默认必填，required = false则不填;不写则是默认值
        log.info("在header1方法中，authorization是{}",authorization);
        return "请求成功";
    }
```

```java
@RequestParam//提取param参数（在url中的），不能对自定义类进行提取，若想进行提取，则将该注解删除
@PostMapping("/hello")
public String query1(@RequestParam(required = false, defaultvalue = "默认值") String authorization){//默认必填，required = false则不填;不写则是默认值
        log.info("在query1方法中，authorization是{}",authorization);
        return "请求成功";
    }
```

```java
@RequestBody//提取body参数，只能对自定义类进行提取
@PostMapping("/hello")
public String body2(@RequestBody Integer age){
    log.info("在body2方法中，age是{}",age);
    return "请求成功";
}
```

```java
@PathVariable//提取path参数
@PostMapping("/hello/{id}")
    public String path1(@PathVariable Long id){
        log.info("在body2方法中，id是{}",id);
        return "请求成功";
    }
```



JAVA Security的认证和授权

> [!info] 关联笔记
> - [[java学习]] --总笔记