---
tags:
  - java高级
  - 笔记
aliases:
  - java进阶
updated: 2026-06-17
---

# 📑 目录

## Part 1：Java 8 核心特性
- [[java高级#1. Lambda 表达式|1. Lambda 表达式]]
  - [[java高级#1.1 基本语法|基本语法]] / [[java高级#1.2 变量捕获|变量捕获]]
- [[java高级#2. 函数式接口|2. 函数式接口]]
  - [[java高级#2.1 四大内置函数式接口|四大内置函数式接口]]
  - [[java高级#2.2 其他常用函数式接口|其他常用函数式接口]]
- [[java高级#3. 方法引用|3. 方法引用 `::`]]
- [[java高级#4. Optional 类|4. Optional 类]]
  - [[java高级#4.1 创建 Optional|创建]] / [[java高级#4.2 消费与转换|消费与转换]]
  - [[java高级#4.3 默认值与异常|默认值与异常]]
- [[java高级#5. Stream API|5. Stream API]]
  - [[java高级#5.1 创建 Stream|创建]] / [[java高级#5.2 中间操作|中间操作]]
  - [[java高级#5.3 终端操作|终端操作]] / [[java高级#5.4 高级收集器|高级收集器]]
  - [[java高级#5.5 并行流|并行流]]
- [[java高级#6. 接口增强|6. 接口增强（默认/静态/私有方法）]]
- [[java高级#7. 新日期时间 API（java.time）|7. 新日期时间 API（java.time）]]
- [[java高级#8. CompletableFuture|8. CompletableFuture 异步编程]]
- [[java高级#9. JUC 并发工具|9. JUC 并发工具增强]]

## Part 2：Java 9-24 精选高频特性
- [[java高级#10. 集合工厂方法（Java 9）|10. 集合工厂方法（Java 9）]]
- [[java高级#11. Stream API 增强（Java 9）|11. Stream API 增强（Java 9）]]
- [[java高级#12. 私有接口方法 try-with-resources 增强（Java 9）|12. 私有接口方法 / try-with-resources（Java 9）]]
- [[java高级#13. var 局部变量类型推断（Java 10）|13. `var` 局部变量推断（Java 10）]]
- [[java高级#14. 局部变量用于 Lambda（Java 11）|14. 局部变量用于 Lambda（Java 11）]]
- [[java高级#15. Switch 表达式（Java 14 正式）|15. Switch 表达式（Java 14）]]
- [[java高级#16. Text Blocks 文本块（Java 15 正式）|16. Text Blocks 文本块（Java 15）]]
- [[java高级#17. Records 记录类（Java 16 正式）|17. Records 记录类（Java 16）]]
- [[java高级#18. 模式匹配 for instanceof（Java 16）|18. 模式匹配 for instanceof（Java 16）]]
- [[java高级#19. Sealed Classes 密封类（Java 17 正式）|19. Sealed Classes 密封类（Java 17）]]
- [[java高级#20. 虚拟线程 Virtual Threads（Java 21）|20. 虚拟线程（Java 21）]]
- [[java高级#21. Sequenced Collections（Java 21）|21. Sequenced Collections（Java 21）]]
- [[java高级#22. Record Patterns（Java 21）|22. Record Patterns（Java 21）]]
- [[java高级#23. Java 22-24 其他精选|23. Java 22-24 其他精选]]

---

> [!info] 前置基础
> 本篇笔记假设你已经掌握了 [[java基础]] 中的面向对象、集合、线程等基础内容。

---

# Part 1：Java 8 核心特性

# 1. Lambda 表达式

Lambda 表达式是 Java 8 引入的最重要的特性，允许把**函数作为方法的参数传递**，使代码更加简洁。

## 1.1 基本语法

```java
(参数列表) -> { 方法体 }

// 完整形式
(int a, int b) -> { return a + b; }

// 省略参数类型（编译器自动推断）
(a, b) -> { return a + b; }

// 只有一行代码时，可省略 {} 和 return
(a, b) -> a + b

// 单个参数可省略 ()
a -> a * 2

// 无参数
() -> System.out.println("Hello")
```

## 1.2 变量捕获

Lambda 可以访问外层作用域的变量，但被捕获的变量必须是 **effectively final**（赋值后不再改变）。

```java
int factor = 10;                                     // effectively final
// factor = 20;                                     // ❌ 不能重新赋值
Function<Integer, Integer> multiplier = n -> n * factor;

// 实例变量和静态变量没有此限制
class Example {
    private int instanceVar = 5;

    public void test() {
        int localVar = 10;
        Consumer<Integer> c = n -> System.out.println(n + instanceVar + localVar);
    }
}
```

## 1.3 常见使用场景

```java
// 1. 线程
new Thread(() -> System.out.println("Lambda 线程")).start();

// 2. 排序
list.sort((s1, s2) -> s1.compareTo(s2));

// 3. 集合遍历
list.forEach(item -> System.out.println(item));

// 4. 自定义函数式接口
Calculator add = (a, b) -> a + b;
```


# 2. 函数式接口

**定义**：只有一个抽象方法的接口（可以有多个默认方法/静态方法）。
使用 `@FunctionalInterface` 注解标记（可选，但推荐）。

```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);

    default void print() { }  // ✅ 默认方法不影响
    static void info() { }    // ✅ 静态方法不影响
}
```

## 2.1 Java 8 内置的四大函数式接口

| 接口 | 抽象方法 | 用途 |
|:---:|:--------:|:----:|
| `Consumer<T>` | `void accept(T t)` | **消费**一个参数，无返回值 |
| `Supplier<T>` | `T get()` | **提供**一个值 |
| `Function<T, R>` | `R apply(T t)` | **转换**一个值为另一个值 |
| `Predicate<T>` | `boolean test(T t)` | **判断**真假，返回 boolean |

```java
// Consumer：消费
Consumer<String> consumer = s -> System.out.println(s);
consumer.accept("Hello");

// Supplier：提供
Supplier<Double> supplier = () -> Math.random();
Double random = supplier.get();

// Function：转换
Function<String, Integer> function = String::length;
Integer len = function.apply("Java");  // 4

// Predicate：判断
Predicate<Integer> predicate = n -> n > 0;
boolean result = predicate.test(5);    // true
```

## 2.2 其他常用函数式接口

| 接口 | 抽象方法 | 用途 |
|:---:|:--------:|:----:|
| `BiFunction<T,U,R>` | `R apply(T t, U u)` | 接收两个参数，返回一个值 |
| `UnaryOperator<T>` | `T apply(T t)` | 参数和返回值类型相同 |
| `BinaryOperator<T>` | `T apply(T t1, T t2)` | 两个同类型参数，返回同类型 |
| `Comparator<T>` | `int compare(T o1, T o2)` | 比较两个对象 |


# 3. 方法引用（Method Reference）—— `::`

Lambda 表达式的简化写法，当 Lambda 体只是调用一个已有方法时使用。

| 类型 | 语法 | 等价 Lambda |
|:----:|:----:|:-----------:|
| 静态方法 | `Class::staticMethod` | `(args) -> Class.staticMethod(args)` |
| 实例方法（特定对象） | `instance::method` | `(args) -> instance.method(args)` |
| 实例方法（任意对象） | `Class::instanceMethod` | `(obj, args) -> obj.method(args)` |
| 构造方法 | `Class::new` | `(args) -> new Class(args)` |

```java
// 静态方法引用
Consumer<String> c = Integer::parseInt;

// 实例方法引用（特定对象）
Supplier<Integer> s = "hello"::length;

// 实例方法引用（任意对象）
Function<String, Integer> f = String::length;
Comparator<Integer> cmp = Integer::compareTo;

// 构造方法引用
Supplier<List<String>> list = ArrayList::new;
```


# 4. Optional 类

`Optional<T>` 是一个容器类，代表一个值存在或不存在，用于**避免 NullPointerException**。不要把它当作字段类型，而是作为**返回类型**使用。

## 4.1 创建 Optional

```java
// 创建空 Optional
Optional<String> empty = Optional.empty();

// 创建非空 Optional（传入 null 会抛 NPE）
Optional<String> nonNull = Optional.of("hello");

// 创建可空 Optional（允许传入 null）
Optional<String> nullable = Optional.ofNullable(someNullableValue);
```

## 4.2 消费与转换

```java
Optional<String> opt = Optional.of("hello");

// ifPresent：值存在时消费
opt.ifPresent(s -> System.out.println(s));

// map：值存在时转换
Optional<Integer> len = opt.map(String::length);

// flatMap：转换结果为 Optional（避免嵌套）
Optional<String> upper = opt.flatMap(s -> Optional.of(s.toUpperCase()));

// filter：按条件过滤
Optional<String> filtered = opt.filter(s -> s.length() > 3);
```

## 4.3 默认值与异常

```java
Optional<String> opt = Optional.empty();

// orElse：值不存在时返回默认值
String v1 = opt.orElse("默认值");

// orElseGet：值不存在时通过 Supplier 提供（延迟计算）
String v2 = opt.orElseGet(() -> expensiveDefault());

// orElseThrow：值不存在时抛异常
String v3 = opt.orElseThrow(() -> new RuntimeException("值不存在"));

// 推荐：先判断再消费
opt.ifPresentOrElse(
    v -> System.out.println("值：" + v),
    () -> System.out.println("无值")       // Java 9+
);
```

### 常见反模式

```java
// ❌ 不推荐：用 isPresent() + get()
if (opt.isPresent()) {
    String v = opt.get();
}

// ✅ 推荐：用 ifPresent / orElse 等函数式写法
opt.ifPresent(v -> process(v));
String v = opt.orElse("default");
```


# 5. Stream API

Stream 是 Java 8 引入的函数式编程 API，用于对集合数据进行**声明式处理**（链式操作）。

**三大特点**：
- **不存储数据**：只进行计算操作
- **函数式编程**：操作结果通常产生一个新的 Stream
- **惰性求值**：中间操作不会立即执行，直到遇到终端操作

## 5.1 操作分类

```
Stream 操作 = 中间操作（返回 Stream） + 终端操作（返回结果/副作用）

中间操作：filter / map / flatMap / distinct / sorted / peek / limit / skip
终端操作：forEach / collect / toList / reduce / count / min / max / anyMatch / allMatch / noneMatch / findFirst / findAny
```

## 5.2 创建 Stream

```java
// 1. 从集合创建（最常用）
Stream<String> stream1 = list.stream();
Stream<String> stream2 = list.parallelStream();      // 并行流

// 2. 从数组创建
Stream<String> stream3 = Arrays.stream(new String[]{"a", "b", "c"});

// 3. 从值创建
Stream<String> stream4 = Stream.of("a", "b", "c");

// 4. 无限流（配合 limit 使用）
Stream<Integer> iterate = Stream.iterate(0, n -> n + 2).limit(10);
Stream<Double> generate = Stream.generate(Math::random).limit(5);
```

## 5.3 中间操作（Intermediate）

### filter —— 过滤
```java
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

### map —— 映射/转换
```java
List<Integer> lengths = words.stream()
    .map(String::length)
    .collect(Collectors.toList());

// mapToInt/mapToLong/mapToDouble 避免自动装箱开销
int sum = words.stream().mapToInt(String::length).sum();
```

### flatMap —— 扁平化映射
```java
List<String> sentences = Arrays.asList("Hello World", "Java Stream");
List<String> allWords = sentences.stream()
    .flatMap(s -> Arrays.stream(s.split(" ")))
    .collect(Collectors.toList());

List<List<Integer>> nested = Arrays.asList(Arrays.asList(1,2), Arrays.asList(3,4));
List<Integer> flat = nested.stream()
    .flatMap(List::stream)
    .collect(Collectors.toList());  // [1, 2, 3, 4]
```

### distinct —— 去重
```java
List<Integer> distinct = numbers.stream().distinct().collect(Collectors.toList());
```

### sorted —— 排序
```java
numbers.stream().sorted().collect(Collectors.toList());                        // 升序
numbers.stream().sorted((a, b) -> b - a).collect(Collectors.toList());         // 降序
people.stream().sorted(Comparator.comparing(Person::getAge).thenComparing(Person::getName));
```

### limit & skip —— 截取（分页）
```java
List<Integer> first3 = numbers.stream().limit(3).collect(Collectors.toList());
List<Integer> after3 = numbers.stream().skip(3).collect(Collectors.toList());

// 分页效果：第 2 页，每页 3 条
List<Integer> page2 = numbers.stream().skip(3).limit(3).collect(Collectors.toList());
```

### peek —— 调试/查看中间结果
```java
List<String> result = Stream.of("one", "two", "three")
    .filter(s -> s.length() > 2)
    .peek(s -> System.out.println("过滤后：" + s))
    .map(String::toUpperCase)
    .peek(s -> System.out.println("转换后：" + s))
    .collect(Collectors.toList());
```

## 5.4 终端操作（Terminal）

### forEach / forEachOrdered
```java
stream.forEach(System.out::println);             // 并行流无序
stream.forEachOrdered(System.out::println);       // 保持顺序
```

### collect —— 收集（最常用）

```java
// 收集到 List
List<String> list = stream.collect(Collectors.toList());
// Java 16+：stream.toList()   （返回不可变 List）

// 收集到 Set
Set<String> set = stream.collect(Collectors.toSet());

// 收集到特定集合类型
ArrayList<String> arrayList = stream.collect(Collectors.toCollection(ArrayList::new));

// 收集到 Map
Map<Integer, String> map = list.stream()
    .collect(Collectors.toMap(String::length, Function.identity(), (v1, v2) -> v1));

// 拼接字符串
String joined = list.stream().collect(Collectors.joining(", ", "[", "]"));
```

### toList()（Java 16+）
```java
List<String> immutableList = stream.toList();  // 返回不可变 List
```

### reduce —— 归约/聚合
```java
Optional<Integer> sum1 = numbers.stream().reduce((a, b) -> a + b);
Integer sum2 = numbers.stream().reduce(0, (a, b) -> a + b);
Optional<Integer> max = numbers.stream().reduce(Integer::max);
```

### count / min / max
```java
long count = list.stream().filter(s -> s.startsWith("a")).count();
Optional<Person> oldest = people.stream().max(Comparator.comparing(Person::getAge));
```

### 匹配与查找
```java
boolean allPositive = numbers.stream().allMatch(n -> n > 0);
boolean anyNegative = numbers.stream().anyMatch(n -> n < 0);
boolean noneZero = numbers.stream().noneMatch(n -> n == 0);

Optional<Integer> first = numbers.stream().filter(n -> n > 3).findFirst();
Optional<Integer> any = numbers.parallelStream().filter(n -> n > 3).findAny();
```

## 5.5 高级收集器（Collectors）

### groupingBy —— 分组
```java
// 按年龄分组
Map<Integer, List<Person>> byAge = people.stream()
    .collect(Collectors.groupingBy(Person::getAge));

// 分组计数
Map<String, Long> countByCity = people.stream()
    .collect(Collectors.groupingBy(Person::getCity, Collectors.counting()));

// 分组后映射
Map<String, List<String>> namesByCity = people.stream()
    .collect(Collectors.groupingBy(Person::getCity,
             Collectors.mapping(Person::getName, Collectors.toList())));

// 多级分组
Map<String, Map<Integer, List<Person>>> multiGroup = people.stream()
    .collect(Collectors.groupingBy(Person::getCity,
             Collectors.groupingBy(Person::getAge)));
```

### partitioningBy —— 分区（二分）
```java
Map<Boolean, List<Person>> partition = people.stream()
    .collect(Collectors.partitioningBy(p -> p.getAge() >= 18));
List<Person> adults = partition.get(true);
```

### summarizingInt —— 统计
```java
IntSummaryStatistics stats = numbers.stream()
    .collect(Collectors.summarizingInt(Integer::intValue));
stats.getSum();      // 总和
stats.getAverage();  // 平均值
stats.getMax();
stats.getMin();
stats.getCount();
```

## 5.6 并行流（Parallel Stream）

```java
// 创建
list.parallelStream().filter(...).collect(...);
list.stream().parallel().filter(...).collect(...);

// 控制并行线程数
System.setProperty("java.util.concurrent.ForkJoinPool.common.parallelism", "8");

// 适合：数据量大、无状态操作、CPU 密集型
// 不适合：数据量小、有共享可变状态、涉及阻塞 I/O
```

## 5.7 综合示例

```java
// 1. 提取不重复的偶数并排序
List<Integer> result = Arrays.asList(3, 6, 2, 8, 2, 6, 1)
    .stream()
    .filter(n -> n % 2 == 0)
    .distinct()
    .sorted()
    .collect(Collectors.toList());  // [2, 6, 8]

// 2. 学生分数段分组
Map<String, List<Student>> gradeMap = students.stream()
    .collect(Collectors.groupingBy(s -> {
        if (s.getScore() >= 90) return "优秀";
        else if (s.getScore() >= 60) return "及格";
        else return "不及格";
    }));

// 3. 部门平均薪资
double avgSalary = employees.stream()
    .filter(e -> e.getDepartment().equals("IT"))
    .mapToDouble(Employee::getSalary)
    .average()
    .orElse(0.0);

// 4. 两个列表交集
List<Integer> intersection = list1.stream()
    .filter(list2::contains)
    .collect(Collectors.toList());

// 5. 统计字符串长度分布
Map<Integer, Long> lenDist = words.stream()
    .collect(Collectors.groupingBy(String::length, Collectors.counting()));
```

## 5.8 注意事项

| 注意点 | 说明 |
|:-----:|:----:|
| 惰性求值 | 没有终端操作时，中间操作不会执行 |
| 一次性 | Stream 只能使用一次，用完即关闭 |
| 不修改原数据 | Stream 操作不影响原始数据源 |
| 无状态 vs 有状态 | filter/map 无状态，sorted/distinct 有状态（需缓冲全部元素） |
| 短路操作 | limit、findFirst、anyMatch 等无需处理所有元素即可返回 |


# 6. 接口增强

Java 8 对接口进行了增强，允许定义**默认方法**和**静态方法**；Java 9 进一步允许**私有方法**。

## 6.1 默认方法（default）
为了解决**接口演进**的兼容性问题：向已有接口（如 `Collection`）添加新方法时不会破坏现有实现类。

```java
interface Vehicle {
    void run();                          // 抽象方法

    default void honk() {                // 默认方法：实现类可不重写
        System.out.println("嘟嘟！");
    }
}

class Car implements Vehicle {
    @Override
    public void run() { /* ... */ }
    // honk() 无需重写，直接继承默认实现
}
```

## 6.2 静态方法（static）
```java
interface MathUtils {
    static int add(int a, int b) {
        return a + b;
    }
}
// 调用：MathUtils.add(1, 2);
```

## 6.3 默认方法的冲突解决

| 优先级 | 规则 |
|:-----:|:----:|
| 1 | **类中的方法优先**：子类中显式定义的方法优先级最高 |
| 2 | **子接口优先**：两个接口存在继承关系时，子接口的默认方法优先 |
| 3 | **必须手动覆盖**：两个无关接口冲突时，实现类必须 `@Override` 解决 |

```java
interface A { default void hello() { System.out.println("A"); } }
interface B { default void hello() { System.out.println("B"); } }

// 冲突：必须手动覆盖
class MyClass implements A, B {
    @Override
    public void hello() {
        A.super.hello();  // 选择调用 A 的默认方法
    }
}

// 类优先于接口
class Base { public void hello() { System.out.println("Base"); } }
class Child extends Base implements A { }  // 继承 Base.hello()
```

## 6.4 私有方法（Java 9+）
```java
interface Logger {
    default void logInfo(String msg) {
        log(msg, "INFO");
    }
    default void logError(String msg) {
        log(msg, "ERROR");
    }
    // 私有方法：复用代码，不对外暴露
    private void log(String msg, String level) {
        System.out.println("[" + level + "] " + msg);
    }
}
```


# 7. 新日期时间 API（java.time）

Java 8 引入 `java.time` 包，解决了旧版 `Date` / `Calendar` 的**线程不安全、设计混乱**等问题。核心设计：**不可变、线程安全、链式调用**。

## 7.1 核心类

| 类 | 说明 | 示例 |
|:--:|:----|:----:|
| `LocalDate` | 日期（不含时间） | `LocalDate.now()` |
| `LocalTime` | 时间（不含日期） | `LocalTime.now()` |
| `LocalDateTime` | 日期 + 时间 | `LocalDateTime.now()` |
| `Instant` | 时间戳（UTC） | `Instant.now()` |
| `Duration` | 时间间隔（秒/纳秒） | `Duration.between(t1, t2)` |
| `Period` | 日期间隔（年/月/日） | `Period.between(d1, d2)` |
| `DateTimeFormatter` | 格式化/解析 | `DateTimeFormatter.ofPattern("yyyy-MM-dd")` |

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

## 7.2 扩展用法

```java
// ZonedDateTime：带时区
ZonedDateTime tokyoTime = ZonedDateTime.now(ZoneId.of("Asia/Tokyo"));

// 时区转换
ZonedDateTime newYork = shanghai.withZoneSameInstant(ZoneId.of("America/New_York"));

// ChronoUnit：时间单位计算
long daysBetween = ChronoUnit.DAYS.between(start, end);

// TemporalAdjusters：日期调整器
LocalDate firstDay = LocalDate.now().with(TemporalAdjusters.firstDayOfMonth());
LocalDate nextMonday = LocalDate.now().with(TemporalAdjusters.next(DayOfWeek.MONDAY));

// MonthDay：判断生日/节日（忽略年份）
MonthDay birthday = MonthDay.of(6, 15);
boolean isBirthday = MonthDay.from(LocalDate.now()).equals(birthday);

// 旧 API 互转
// Date → LocalDateTime
LocalDateTime ldt = new Date().toInstant()
    .atZone(ZoneId.systemDefault())
    .toLocalDateTime();
// LocalDateTime → Date
Date date = Date.from(ldt.atZone(ZoneId.systemDefault()).toInstant());
// LocalDate → java.sql.Date
java.sql.Date sqlDate = java.sql.Date.valueOf(localDate);
```


# 8. CompletableFuture

`CompletableFuture` 是对 `Future` 的增强，支持**异步编程**和**回调编排**，天然支持函数式编程。

## 8.1 基本使用

```java
// 1. 直接创建已完成的 Future
CompletableFuture<String> completed = CompletableFuture.completedFuture("结果");

// 2. 异步执行（无返回值）
CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
    System.out.println("异步任务执行中...");
});

// 3. 异步执行（有返回值）
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    TimeUnit.SECONDS.sleep(1);
    return "任务结果";
});

// 4. 获取结果（阻塞）
String result = future.get();              // 抛受检异常
String result = future.join();             // 抛非受检异常（推荐）
```

## 8.2 回调编排

```java
// thenApply —— 转换结果（同步）
CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> "hello")
    .thenApply(String::length);

// thenAccept —— 消费结果（无返回值）
CompletableFuture.supplyAsync(() -> "hello")
    .thenAccept(System.out::println);

// thenRun —— 执行 Runnable（不关心结果）
CompletableFuture.supplyAsync(() -> "hello")
    .thenRun(() -> System.out.println("任务完成"));

// exceptionally —— 异常恢复
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    if (Math.random() > 0.5) throw new RuntimeException("出错了");
    return "成功";
}).exceptionally(ex -> "默认值：" + ex.getMessage());

// handle —— 无论成功失败都处理
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    if (Math.random() > 0.5) throw new RuntimeException("出错了");
    return "成功";
}).handle((result, ex) -> {
    return ex != null ? "处理异常" : result;
});
```

## 8.3 多任务组合

```java
// thenCompose —— 依赖组合（flatMap）
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "hello")
    .thenCompose(s -> CompletableFuture.supplyAsync(() -> s + " world"));

// thenCombine —— 并行组合（两个独立任务）
CompletableFuture<String> f1 = CompletableFuture.supplyAsync(() -> "Hello");
CompletableFuture<String> f2 = CompletableFuture.supplyAsync(() -> "World");
CompletableFuture<String> combined = f1.thenCombine(f2, (a, b) -> a + " " + b);

// allOf —— 等待所有完成
CompletableFuture<Void> all = CompletableFuture.allOf(f1, f2);
all.join();  // 阻塞直到全部完成

// anyOf —— 任意一个完成
CompletableFuture<Object> any = CompletableFuture.anyOf(f1, f2);
```

## 8.4 实战：批量查询

```java
// 模拟：并发查询多个用户信息
List<Integer> userIds = Arrays.asList(1, 2, 3, 4, 5);

List<CompletableFuture<User>> futures = userIds.stream()
    .map(id -> CompletableFuture.supplyAsync(() -> queryUserById(id)))
    .collect(Collectors.toList());

// 等待所有完成并收集结果
List<User> users = futures.stream()
    .map(CompletableFuture::join)
    .collect(Collectors.toList());

// 超时控制（Java 9+）
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> longTask())
    .orTimeout(3, TimeUnit.SECONDS);       // 超时抛 TimeoutException

// 默认值（Java 9+）
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> longTask())
    .completeOnTimeout("超时默认值", 3, TimeUnit.SECONDS);
```


# 9. JUC 并发工具

## 9.1 线程安全集合对比

| 类 | 线程安全机制 | 替代方案 |
|:--:|:-----------:|:-------:|
| `ConcurrentHashMap` | CAS + synchronized（细粒度锁） | Hashtable |
| `CopyOnWriteArrayList` | 写时复制（读多写少） | Vector |
| `CopyOnWriteArraySet` | 基于 CopyOnWriteArrayList | synchronizedSet |
| `ConcurrentLinkedQueue` | CAS 无锁算法 | — |
| `BlockingQueue` | ReentrantLock + Condition | 生产者-消费者专用 |

```java
// ConcurrentHashMap 常用 API
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
map.put("key", 1);
map.putIfAbsent("key", 2);                         // 不存在才放入
map.computeIfPresent("key", (k, v) -> v + 1);      // 存在则计算
map.computeIfAbsent("key2", k -> computeValue(k)); // 不存在则计算

// CopyOnWriteArrayList（读多写少场景）
CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
// 每次写操作都会复制底层数组，适合读远多于写的场景
```

## 9.2 原子类（Atomic）

```java
AtomicInteger count = new AtomicInteger(0);
count.incrementAndGet();       // ++i（线程安全）
count.getAndIncrement();       // i++
count.addAndGet(5);            // += 5
count.compareAndSet(10, 20);   // CAS 操作

// 性能：AtomicInteger > synchronized > Lock（低竞争下）
```

## 9.3 同步工具类

```java
// CountDownLatch：等待 N 个线程完成
CountDownLatch latch = new CountDownLatch(3);
// 每个线程结束时 latch.countDown()
latch.await();  // 阻塞直到 count 降为 0

// CyclicBarrier：N 个线程到达屏障后同时继续
CyclicBarrier barrier = new CyclicBarrier(3, () -> System.out.println("全部到达"));
// 每个线程执行到某点后 barrier.await()

// Semaphore：控制并发访问数（限流）
Semaphore semaphore = new Semaphore(3);  // 最多 3 个线程同时访问
semaphore.acquire();
// ... 访问共享资源 ...
semaphore.release();
```

---

# Part 2：Java 9-24 精选高频特性

# 10. 集合工厂方法（Java 9）

快速创建不可变集合：

```java
// Java 9 之前：Arrays.asList 或 匿名内部类
List<String> list = Arrays.asList("a", "b", "c");  // 可变，但不可增删

// Java 9+：of() 工厂方法（返回不可变集合）
List<String> list = List.of("a", "b", "c");
Set<String> set = Set.of("a", "b", "c");
Map<String, Integer> map = Map.of("a", 1, "b", 2);

// Map 支持多参数
Map<String, Integer> map2 = Map.ofEntries(
    Map.entry("a", 1),
    Map.entry("b", 2)
);

// 特点：返回的集合不可变（不可增/删/改），允许 null 个元素（但不是 null 元素）
// 注意：List.of() 不接受 null 元素
```

应用场景：定义常量集合、测试数据、配置项。


# 11. Stream API 增强（Java 9）

```java
// takeWhile：从开头取，遇到不满足条件就停止
Stream.of(1, 2, 3, 4, 5, 6)
    .takeWhile(n -> n < 4)
    .collect(Collectors.toList());      // [1, 2, 3]

// dropWhile：从开头丢弃，遇到不满足条件开始保留
Stream.of(1, 2, 3, 4, 5, 6)
    .dropWhile(n -> n < 4)
    .collect(Collectors.toList());      // [4, 5, 6]

// ofNullable：安全创建 Stream（避免 NPE）
Stream<String> stream = Stream.ofNullable(someNullableString);
// 等价于：someNullableString == null ? Stream.empty() : Stream.of(someNullableString)

// iterate 重载：带终止条件
Stream.iterate(0, n -> n < 100, n -> n + 1)
    .forEach(System.out::println);      // 0, 1, 2, ..., 99
```


# 12. 私有接口方法 / try-with-resources 增强（Java 9）

## 私有接口方法
已在 [[java高级#6.4 私有方法（Java 9+）]] 中介绍。

## try-with-resources 增强

```java
// Java 7：必须在该语句中声明变量
try (Resource r = new Resource()) { ... }

// Java 9+：可以使用 effectively final 的变量
Resource r = new Resource();
try (r) {                           // ✅ 编译通过
    // 使用 r
}
```


# 13. `var` 局部变量类型推断（Java 10）

让编译器根据初始值自动推断类型，减少样板代码。

```java
// 传统写法
List<String> list = new ArrayList<>();
Map<String, List<Integer>> map = new HashMap<>();

// 使用 var
var list = new ArrayList<String>();          // 推断为 ArrayList<String>
var map = new HashMap<String, List<Integer>>();
var number = 42;                             // int
var text = "hello";                          // String
var stream = list.stream();                  // Stream<String>

// 适用于：泛型嵌套、循环、Lambda 参数类型过长时
var person = new Person("小明", 18);
for (var entry : map.entrySet()) {
    // ...
}

// 限制：不能用于字段、方法参数、返回值类型、Lambda 表达式
// var name;                    // ❌ 必须初始化
// var nullValue = null;        // ❌ 不能推断 null
// var arr = {1, 2, 3};         // ❌ 不能推断数组初始值
```

**最佳实践**：`var` 让代码更简洁，但不要滥用。当类型明显时使用（如 `new` 表达式右侧），当可读性受损时避免（如链式调用返回值不明确时）。


# 14. 局部变量用于 Lambda（Java 11）

在 Lambda 表达式中使用 `var` 声明参数，可以配合注解使用。

```java
// Java 11 之前：不能加注解
list.sort((@NotNull String s1, String s2) -> s1.length() - s2.length());

// Java 11+：var + 注解
list.sort((@NotNull var s1, var s2) -> s1.length() - s2.length());

// 注意：Lambda 参数使用 var 时，要么全用 var，要么全不用
// list.sort((var s1, s2) -> ...);  // ❌ 编译错误
```


# 15. Switch 表达式（Java 14 正式）

Switch 从**语句**升级为**表达式**，支持返回值、箭头语法、模式匹配。

```java
// 传统 Switch（容易漏 break）
String result;
switch (day) {
    case MONDAY:
    case FRIDAY:
        result = "工作日";
        break;
    case SATURDAY:
    case SUNDAY:
        result = "休息日";
        break;
    default:
        result = "未知";
}

// Switch 表达式（箭头语法，自动 break，可返回值）
String result = switch (day) {
    case MONDAY, FRIDAY -> "工作日";
    case SATURDAY, SUNDAY -> "休息日";
    default -> "未知";
};

// Switch 表达式（yield 返回值，适合需要代码块的场景）
String result = switch (day) {
    case MONDAY, FRIDAY:
        yield "工作日";
    case SATURDAY, SUNDAY:
        yield "休息日";
    default:
        yield "未知";
};

// 枚举穷举后可以省略 default
enum Day { MON, TUE, WED, THU, FRI, SAT, SUN }
String type = switch (day) {
    case MON, TUE, WED, THU, FRI -> "工作日";
    case SAT, SUN -> "休息日";
    // 不需要 default
};
```


# 16. Text Blocks 文本块（Java 15 正式）

用三重引号 `"""` 表示多行字符串，自动处理缩进和转义。

```java
// Java 15 之前（恶心转义）
String json = "{\n" +
    "  \"name\": \"小明\",\n" +
    "  \"age\": 18\n" +
    "}";

// Text Blocks
String json = """
    {
      "name": "小明",
      "age": 18
    }
    """;

// HTML 模板
String html = """
    <html>
        <body>
            <h1>Hello</h1>
        </body>
    </html>
    """;

// SQL 语句
String sql = """
    SELECT id, name, age
    FROM users
    WHERE age > 18
    ORDER BY age DESC
    """;

// 保留尾部空格：\s（不会自动去除）
// 换行拼接：\（行尾反斜杠表示不换行）
String text = """
    hello \
    world""";   // "hello world"
```

**自动缩进**：以最左侧的公共缩进为基准。`"""` 闭合标签位置决定去除多少前导空白。


# 17. Records 记录类（Java 16 正式）

用于定义**纯数据载体**的类，自动生成构造器、getter、equals、hashCode、toString。

```java
// 传统 POJO（约 50 行样板代码）
public class Point {
    private final int x;
    private final int y;
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    public int x() { return x; }
    public int y() { return y; }
    // equals / hashCode / toString ...
}

// Record（一行搞定）
public record Point(int x, int y) { }

// 使用
Point p = new Point(3, 4);
System.out.println(p.x());      // 3（注意不是 getX()）
System.out.println(p.toString());  // Point[x=3, y=4]
System.out.println(p.equals(new Point(3, 4)));  // true

// 也可以添加自定义方法、验证逻辑
public record Person(String name, int age) {
    // 紧凑构造器（编译器自动赋值）
    public Person {
        if (age < 0) {
            throw new IllegalArgumentException("年龄不能为负");
        }
    }

    // 可以添加实例方法
    public String greeting() {
        return "你好，我是" + name;
    }

    // 可以添加静态方法
    public static Person of(String name, int age) {
        return new Person(name, age);
    }
}

// Records 配合 Spring Boot 的 DTO 非常合适
// 注意：Record 是 final 的，不能继承，也不能被继承
```

**最佳实践**：DTO、VO、API 响应、不可变数据传输对象。


# 18. 模式匹配 for instanceof（Java 16）

简化类型检查和类型转换。Java 21 进一步支持**记录模式**。

```java
// 传统写法
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.length());
}

// 模式匹配（Java 16+）
if (obj instanceof String s) {
    System.out.println(s.length());  // 直接使用 s
}

// 组合条件
if (obj instanceof String s && s.length() > 5) {
    System.out.println(s.toUpperCase());
}

// 配合 Switch（Java 17+ 预览，Java 21 正式）
String formatted = switch (obj) {
    case Integer i -> String.format("int %d", i);
    case String s  -> String.format("string %s", s);
    case null      -> "null";              // null 处理
    default        -> "unknown";
};
```


# 19. Sealed Classes 密封类（Java 17 正式）

限制哪些类可以继承或实现某个类/接口，提供更精确的继承控制。

```java
// 定义密封接口
public sealed interface Shape permits Circle, Rectangle, Triangle { }

// 许可子类（必须用 sealed、non-sealed 或 final 修饰）
public final class Circle implements Shape { }      // 不可再继承

public non-sealed class Rectangle implements Shape { }  // 开放继承

public sealed class Triangle implements Shape permits EquilateralTriangle { }
public final class EquilateralTriangle extends Triangle { }

// 密封类（abstract 也可以密封）
public abstract sealed class Animal permits Dog, Cat { }

// 密封 + Switch 的完美配合（Java 21）
String area = switch (shape) {
    case Circle c    -> Math.PI * c.radius() * c.radius();
    case Rectangle r -> r.width() * r.height();
    case Triangle t  -> t.base() * t.height() / 2;
    // 穷举了所有子类，无需 default
};
```

**应用场景**：领域模型中的有限类型（如支付方式、订单状态）、权限控制、安全敏感的类层次。


# 20. 虚拟线程 Virtual Threads（Java 21）

轻量级线程，由 JVM 管理而非 OS，可以创建**数百万个**。基于**结构化并发**，极大简化高并发编程。

```java
// 传统线程（OS 线程，数量有限）
Thread t = new Thread(() -> {
    // 处理请求
});
t.start();

// 虚拟线程（Java 21）
Thread vThread = Thread.startVirtualThread(() -> {
    System.out.println("虚拟线程运行中");
});

// 使用 Executors 创建虚拟线程池
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    for (int i = 0; i < 10000; i++) {
        executor.submit(() -> {
            // 处理任务...
            Thread.sleep(1000);  // 虚拟线程在 sleep 时会释放 OS 线程
            return "done";
        });
    }
}  // 自动关闭，等待所有任务完成

// 对比：传统线程池无法同时处理 10000 个长期阻塞的任务
// 虚拟线程：可以轻松处理，每个虚拟线程消耗约 1KB 内存

// 注意事项：
// 1. 虚拟线程适用于 IO 密集型任务，不适用于 CPU 密集型
// 2. 避免 synchronized（会钉住虚拟线程），用 ReentrantLock 替代
// 3. 不要池化虚拟线程（每个任务新建即可）
// 4. ThreadLocal 在虚拟线程中仍然可用，但创建大量虚拟线程时需注意内存
```


# 21. Sequenced Collections（Java 21）

为集合接口增加了**有序访问**的方法，统一了 List、Deque、SortedSet、LinkedHashMap 等的 API。

```java
// 新引入的接口：SequencedCollection、SequencedSet、SequencedMap

// SequencedCollection（List 和 Deque 实现）
SequencedCollection<String> seq = new ArrayList<>();
seq.addFirst("a");           // 开头添加
seq.addLast("z");            // 末尾添加
String first = seq.getFirst();
String last = seq.getLast();
seq.removeFirst();
seq.removeLast();
SequencedCollection<String> reversed = seq.reversed();  // 逆序视图

// SequencedMap
SequencedMap<String, Integer> map = new LinkedHashMap<>();
map.putFirst("a", 1);
map.putLast("z", 26);
map.firstEntry();
map.lastEntry();
map.pollFirstEntry();
map.pollLastEntry();
SequencedMap<String, Integer> reversedMap = map.reversed();
```

**优势**：不再需要 `((Deque) list).addFirst()` 或通过 `keySet().iterator().next()` 获取第一个键。


# 22. Record Patterns（Java 21）

与模式匹配 for instanceof 和 Switch 结合，可以**解构 Record**。

```java
record Point(int x, int y) { }
record Line(Point start, Point end) { }

// 嵌套解构
if (obj instanceof Line(Point(int x1, int y1), Point(int x2, int y2))) {
    System.out.println("起点：" + x1 + "," + y1);
    System.out.println("终点：" + x2 + "," + y2);
}

// 配合 Switch
String desc = switch (obj) {
    case Point(int x, int y)          -> "点 (" + x + ", " + y + ")";
    case Line(Point s, Point e)       -> "线段";
    case null                         -> "null";
    default                           -> "未知";
};
```


# 23. Java 22-24 其他精选

## 语句前的超级构造函数（Java 22）
```java
// 传统：super() 必须在构造器第一行
public class Child extends Parent {
    public Child(int value) {
        super(value * 2);  // 必须第一行
    }
}

// 如果需要在调用 super 前做一些验证，以前做不到
// Java 22+（预览）开始允许在 super() 前添加语句
```

## Stream 的 gather 方法（Java 22 预览）
```java
// gather 允许自定义中间操作，比现有中间操作更灵活
// 示例：自定义窗口操作
// stream.gather(myCustomGather).collect(...)
// （仍在预览阶段，后续版本可能调整）
```

## 未命名模式和变量（Java 22）
```java
// 用 _ 表示不关心的变量
if (obj instanceof Point(int x, int _)) {
    System.out.println("x = " + x);  // 不关心 y
}

// 循环中不使用的变量
map.entrySet().forEach(entry -> {
    // ...
    _ = someMethod();  // 忽略返回值
});
```

## 字符串模板（Java 21 预览→后续调整）
```java
// 注意：原始 STR 模板语法在后续版本中有调整
// 建议参考当前 JDK 文档使用最新 API
String name = "小明";
// 使用字符串拼接或 String.format 仍是最稳定的方案
String msg = STR."Hello \{name}";  // 预览语法，API 可能有变化
```

> [!info] 保持更新
> Java 新版本每 6 个月发布一次，建议关注 [OpenJDK 发布说明](https://openjdk.org/projects/jdk/) 获取最新特性。


# 关联笔记

>[!info] 关联笔记
>
>  [[java基础]] —— Java 入门基础（变量、OOP、集合、线程、IO、反射）
>  [[java学习]] —— Java 学习总索引
>  [[java_web]] —— Java Web 开发
