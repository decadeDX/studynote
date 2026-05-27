---
updated: 2026-05-02 10:48:35
focused: 00:00:25
---
# 总目录：
[[java学习]]
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
### 向上转型
必须是**继承关系**才能转

```java
Animal animal = new Dog();
```
### 向下转型
```java
if(animal instanceof Dog){
    Dog dog = (Dog) animal;
}
```
# 3.修饰符
## 非访问修饰符：

|     关键字      | 核心含义 |     修饰对象      |      关键点       |
| :----------: | :--: | :-----------: | :------------: |
|    final     | 不可变  |    类、方法、变量    | 不能继承、不能重写、不能修改 |
|    static    | 属于类  | 变量、方法、代码块、内部类 |  全局唯一，类名直接调用   |
|   abstract   | 未实现  |     类、方法      |  不能实例化，必须子类实现  |
| synchronized | 线程同步 |    方法、代码块     |   多线程排队，保证安全   |

一个类不能同时被 abstract 和 final 修饰。如果一个类包含抽象方法，那么该类一定要声明为抽象类，否则将出现编译错误。
抽象类可以包含抽象方法和非抽象方法。
## 访问修饰符：

 default, public , protected, private

- 父类中声明为 public 的方法在子类中也必须为 public。
- 父类中声明为 protected 的方法在子类中要么声明为 protected，要么声明为 public，不能声明为 private。
- 父类中声明为 private 的方法，不能够被子类继承。



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
## 1.对象内存分布
![对象内存分布](picture/java/对象内存分布.png)
## 2.属性
语法： 访问修饰符 属性类型  属性名；
## 3.方法传参机制
基本数据类型，传递的是值（值拷贝），形参的任何改变不影响实参
引用类型，传递到是地址，形参可以改变实参

## 4.重载
同名方法中，参数列表不一致

## 5.可变参数
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

## 6.构造器
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

## 7.this关键字
this代表当前对象，使用this解决前面变量命名问题
## 8.包的命名
命名规则：
- 只能包含数字、字母、下划线、小圆点，但不能使用数字开头，不能是关键字或保留字
- 一般是com.公司名.项目名.业务模块名
# 8.==封装==
封装就是把抽象出的数据（属性）和对数据的操作（方法）封装在一起，数据被保护在内部，程序其他部分只有通过被授权的操作（方法），才能对数据进行操作。
步骤：
- 私有化属性
- 设置公共set方法，对属性判断并赋值
- 设置公共get方法，获取属性的值
# 9.继承
extends 关键字
1. 子类继承了所有的属性和方法，==非私有的属性和方法可以在子类直接访问==，但是私有属性和方法不能再子类直接访问，要通过父类提供的公共方法去访问
2. 子类必须调用父类的构造器，完成父类的初始化
3. 先创建父类，再创建子类；如果父类没有无参构造器，必须用super指明用哪个构造器完成对父类的初始化工作，否则，编译不通过
4. 如希望指定调用父类的某个构造器，需要显示调用super()
5. super和this在使用时都只能放在构造器的第一行，因此两个方法不能共存在一个构造器中

# 7.接口

是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

### 接口与类相似点：

- 一个接口可以有多个方法。
- 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
- 接口的字节码文件保存在 .class 结尾的文件中。
- 接口相应的字节码文件必须在与包名称相匹配的目录结构中。

### 接口与类的区别：

- 接口不能用于实例化对象。
- 接口没有构造方法。
- 接口中所有的方法必须是抽象方法，Java 8 之后 接口中可以使用 default 关键字修饰的非抽象方法。
- 接口不能包含成员变量，除了 static 和 final 变量。
- 接口不是被类继承了，而是要被类实现。
- 接口支持多继承。

### 接口特性

- 接口中每一个方法也是隐式抽象的,接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）。
- 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
- 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。

### 抽象类和接口的区别

- 1. 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。
- 2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。
- 3. 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
- 4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。



**注**：JDK 1.8 以后，接口里可以有静态方法和方法体了。

**注**：JDK 1.8 以后，接口允许包含具体实现的方法，该方法称为"默认方法"，默认方法使用 default 关键字修饰。更多内容可参考 [Java 8 默认方法](https://www.runoob.com/java/java8-default-methods.html)。

**注**：JDK 1.9 以后，允许将方法定义为 private，使得某些复用的代码不会把方法暴露出去。更多内容可参考 [Java 9 私有接口方法](https://www.runoob.com/java/java9-private-interface-methods.html)。



# 7.类的五大成员

属性、方法、构造器、代码块、内部类9 







# Lombok工具：

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

