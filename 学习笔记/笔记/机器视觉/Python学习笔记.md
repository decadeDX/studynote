---
tags:
  - python
  - 笔记
created: 2026-06-10
---

> 聚焦高级特性，基础语法仅作速览。部分内容结合 [[机器视觉]] / [[深度学习笔记]] 实际场景。

---

## 目录

- [[#一、基础语法速览]]
  - [[#1.1 变量与数据类型]]
  - [[#1.2 控制流]]
  - [[#1.3 函数定义]]
  - [[#1.4 内置数据结构速查]]
  - [[#1.5 文件读写]]
- [[#二、高级特性]]
  - [[#2.1 切片 (Slice)]]
  - [[#2.2 推导式 (Comprehensions)]]
  - [[#2.3 迭代器与生成器]]
  - [[#2.4 装饰器 (Decorator)]]
  - [[#2.5 上下文管理器 (Context Manager)]]
  - [[#2.6 Lambda 与高阶函数]]
  - [[#2.7 面向对象高级特性]]
  - [[#2.8 类型注解 (Type Hints)]]
  - [[#2.9 并发编程概览]]
  - [[#2.10 实用标准库]]
  - [[#2.11 NumPy 核心用法]]
- [[#三、常见问题与陷阱]]
  - [[#3.1 可变默认参数]]
  - [[#3.2 浅拷贝 vs 深拷贝]]
  - [[#3.3 GIL 与性能]]
  - [[#3.4 循环中修改列表]]
- [[#附录：速查表]]
  - [[#A. 常用内置函数]]
  - [[#B. pip 常用命令]]
  - [[#C. 虚拟环境]]

---

# 一、基础语法速览

## 1.1 变量与数据类型

Python 是**动态类型**语言，变量无需声明类型：

```python
# 基本类型
a = 10          # int
b = 3.14        # float
c = 1 + 2j      # complex
s = "hello"     # str
flag = True     # bool
none_val = None # NoneType

# 类型检查与转换
print(type(a))          # <class 'int'>
print(isinstance(a, int))  # True
s = str(100)            # "100"
n = int("42")           # 42
```

## 1.2 控制流

```python
# if-elif-else
x = 85
if x >= 90:
    grade = "A"
elif x >= 80:
    grade = "B"
else:
    grade = "C"

# for 循环 — 遍历可迭代对象
for i in range(5):
    print(i)          # 0 1 2 3 4

for item in [1, 2, 3]:
    print(item)

# while 循环
count = 0
while count < 3:
    print(count)
    count += 1

# 三元表达式
result = "偶数" if x % 2 == 0 else "奇数"
```

## 1.3 函数定义

```python
def greet(name, greeting="Hello"):
    """返回问候语（docstring）"""
    return f"{greeting}, {name}!"

print(greet("World"))               # Hello, World!
print(greet("Python", "Hi"))        # Hi, Python!

# 可变参数
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3, 4))  # 10

# 关键字参数
def print_info(**kwargs):
    for k, v in kwargs.items():
        print(f"{k}: {v}")

print_info(name="Alice", age=25)
```

## 1.4 内置数据结构速查

|     | 类型      | 创建          | 特点     | 示例              |
| --- | ------- | ----------- | ------ | --------------- |
|     | `list`  | `[1, 2, 3]` | 有序、可变  | `lst.append(4)` |
|     | `tuple` | `(1, 2, 3)` | 有序、不可变 | `t[0]`          |
|     | `dict`  | `{"a": 1}`  | 键值对、可变 | `d.get("a", 0)` |
|     | `set`   | `{1, 2, 3}` | 无序、唯一  | `s.add(4)`      |

```python
# list 常用操作
lst = [1, 2, 3]
lst.append(4)       # [1, 2, 3, 4]
lst.extend([5, 6])  # [1, 2, 3, 4, 5, 6]
lst.insert(0, 0)    # [0, 1, 2, 3, 4, 5, 6]
lst.pop()           # 6, lst 变为 [0, 1, 2, 3, 4, 5]

# dict 常用操作
d = {"a": 1, "b": 2}
d["c"] = 3
print(d.get("z", "missing"))  # missing
for k, v in d.items():
    print(k, v)

# set 去重与集合运算
a = {1, 2, 3}
b = {3, 4, 5}
print(a & b)  # {3}   交集
print(a | b)  # {1,2,3,4,5}  并集
print(a - b)  # {1, 2}  差集
```

## 1.5 文件读写

```python
# 写文件
with open("test.txt", "w", encoding="utf-8") as f:
    f.write("Hello Python\n")
    f.write("第二行")

# 读文件
with open("test.txt", "r", encoding="utf-8") as f:
    content = f.read()           # 读取全部
    # lines = f.readlines()      # 读取所有行
    # for line in f:             # 逐行迭代
    #     print(line.strip())
```

---

# 二、高级特性

## 2.1 切片 (Slice)

切片是 Python 最强大的特性之一，语法为 `[start:stop:step]`。

### 基本规则

- **stop 是"切到不取"的右边界**（左闭右开区间 `[start, stop)`）
- 正索引从左数 `0, 1, 2, ...`；负索引从右数 `-1, -2, ...`
- 省略 start 表示从开头；省略 stop 表示到末尾
- `[:]` 常用于**浅拷贝**；`[::-1]` 表示**整段反转**

```python
lst = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(lst[2:5])      # [2, 3, 4]   索引2到4
print(lst[5:])       # [5, 6, 7, 8, 9]  从5到末尾
print(lst[:5])       # [0, 1, 2, 3, 4]  从开头到4
print(lst[::2])      # [0, 2, 4, 6, 8]  步长为2
print(lst[1::2])     # [1, 3, 5, 7, 9]  从索引1开始，步长为2
print(lst[::-1])     # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]  反转
print(lst[-3:])      # [7, 8, 9]  最后3个
print(lst[:-3])      # [0, 1, 2, 3, 4, 5, 6]  除最后3个
```

### 字符串切片

```python
s = "Hello Python"
print(s[:5])         # "Hello"
print(s[::-1])       # "nohtyP olleH"  字符串反转
print(s[::2])        # "HloPto"  每隔一个字符

# 实战：判断回文
def is_palindrome(s):
    return s == s[::-1]

print(is_palindrome("上海自来水来自海上"))  # True
```

### NumPy 数组切片（重要）

> NumPy 切片返回**视图（view）**，而非拷贝——修改切片会影响原数组。这是与 Python 列表的核心区别。

```python
import numpy as np

arr = np.arange(12).reshape(3, 4)
# array([[ 0,  1,  2,  3],
#        [ 4,  5,  6,  7],
#        [ 8,  9, 10, 11]])

print(arr[0, :])       # [0 1 2 3]   第一行
print(arr[:, 1])       # [1 5 9]     第二列
print(arr[1:, 1:3])    # [[5 6]      子矩阵
                       #  [9 10]]

# 步长切片
print(arr[::2, ::2])   # [[0 2]      每隔一行/列
                       #  [8 10]]

# 视图 vs 拷贝
sub = arr[:2, :2]      # 视图
sub[0, 0] = 99
print(arr[0, 0])       # 99 — 原数组也被修改！

# 强制拷贝
sub_copy = arr[:2, :2].copy()  # 独立拷贝
```

---

## 2.2 推导式 (Comprehensions)

推导式是 Python 表达力最强的语法之一，用一条语句生成集合。

### 列表推导式

```python
# 基本形式
squares = [x**2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# 带条件过滤
evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# if-else 三元（注意位置不同）
labels = ["偶数" if x % 2 == 0 else "奇数" for x in range(5)]
# ['偶数', '奇数', '偶数', '奇数', '偶数']

# 实战：展平二维列表
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [x for row in matrix for x in row]
# [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 字典推导式

```python
# 键值互换
d = {"a": 1, "b": 2, "c": 3}
swapped = {v: k for k, v in d.items()}
# {1: 'a', 2: 'b', 3: 'c'}

# 条件过滤
filtered = {k: v for k, v in d.items() if v > 1}
# {'b': 2, 'c': 3}

# 实战：词频统计
words = ["apple", "banana", "apple", "cherry", "banana", "apple"]
freq = {w: words.count(w) for w in set(words)}
# {'apple': 3, 'banana': 2, 'cherry': 1}
```

### 集合推导式

```python
# 去重 + 转换
nums = [1, -2, 3, -4, 2, 3]
abs_set = {abs(x) for x in nums}
# {1, 2, 3, 4}
```

### 生成器表达式

> 用 `()` 替代 `[]`，**惰性求值**，节省内存。适合处理大量数据。

```python
# 生成器表达式 — 不立即计算
gen = (x**2 for x in range(10**6))  # 几乎不占内存
print(next(gen))  # 0
print(next(gen))  # 1

# 实战：求大文件的总行数（不加载到内存）
# total = sum(1 for line in open("large_file.txt"))
```

---

## 2.3 迭代器与生成器

### 可迭代对象 vs 迭代器

```python
# 可迭代对象 (Iterable)：能用于 for 循环，具有 __iter__ 方法
lst = [1, 2, 3]
print(hasattr(lst, '__iter__'))   # True

# 迭代器 (Iterator)：具有 __next__ 方法
it = iter(lst)
print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
# next(it) → StopIteration

# 自定义迭代器
class Countdown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        self.current -= 1
        return self.current + 1

for n in Countdown(3):
    print(n)  # 3 2 1
```

### 生成器：yield

> 生成器是**创建迭代器的最简方式**。函数中只要出现 `yield`，就变成了生成器函数。

```python
# 简单生成器
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for num in countdown(3):
    print(num)  # 3 2 1

# 状态保存 — 每次 yield 暂停，下次从暂停处继续
gen = countdown(3)
print(next(gen))  # 3
print(next(gen))  # 2
print(next(gen))  # 1
```

### yield from

```python
# 委托给子生成器
def chain(*iterables):
    for it in iterables:
        yield from it  # 等价于 for x in it: yield x

print(list(chain("AB", "CD", "EF")))
# ['A', 'B', 'C', 'D', 'E', 'F']
```

### 实战：逐行读取大文件

```python
def read_large_file(file_path):
    """生成器：逐行 yield，不会将整个文件读入内存"""
    with open(file_path, "r", encoding="utf-8") as f:
        for line in f:
            yield line.strip()

# 处理 GB 级文件
# for line in read_large_file("huge_log.txt"):
#     if "ERROR" in line:
#         print(line)
```

### 实战：无限序列生成

```python
def fibonacci():
    """无限斐波那契数列"""
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

fib = fibonacci()
print([next(fib) for _ in range(10)])
# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

---

## 2.4 装饰器 (Decorator)

装饰器本质是**接收函数、返回新函数的高阶函数**。用 `@` 语法糖应用。

### 前置知识：函数是一等对象

```python
def greet():
    print("Hello!")

f = greet          # 函数可以赋值给变量
f()               # Hello!

def runner(func):
    func()         # 函数可以作为参数

runner(greet)     # Hello!

def make_multiplier(n):
    def multiply(x):
        return x * n
    return multiply  # 函数可以返回函数（闭包）

double = make_multiplier(2)
print(double(5))  # 10
```

### 简单装饰器

```python
def my_decorator(func):
    def wrapper():
        print("=== 调用前 ===")
        func()
        print("=== 调用后 ===")
    return wrapper

@my_decorator
def say_hello():
    print("Hello World!")

say_hello()
# === 调用前 ===
# Hello World!
# === 调用后 ===
```

### 保留函数元信息：`@wraps`

> 装饰器会覆盖原函数的 `__name__`、`__doc__` 等元信息，必须用 `functools.wraps` 修复。

```python
from functools import wraps

def my_decorator(func):
    @wraps(func)  # 保留原函数元信息
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper
```

### 带参数的装饰器

```python
def repeat(n):
    """装饰器工厂：返回真正的装饰器"""
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Python")  # 打印3次
```

### 实战：计时器装饰器

```python
import time

def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        result = func(*args, **kwargs)
        elapsed = time.perf_counter() - start
        print(f"{func.__name__} 耗时: {elapsed:.6f}s")
        return result
    return wrapper

@timer
def slow_sum(n):
    return sum(i**2 for i in range(n))

slow_sum(10_000_000)
# slow_sum 耗时: 0.xxxxxxs
```

### 实战：LRU 缓存装饰器

```python
from functools import lru_cache

@lru_cache(maxsize=128)
def fib(n):
    """计算第 n 个斐波那契数（带缓存）"""
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)

print(fib(100))  # 即使递归100层，也瞬间返回

# 查看缓存统计
print(fib.cache_info())
# CacheInfo(hits=98, misses=101, maxsize=128, currsize=101)
```

### 类装饰器

```python
class Singleton:
    """将类变为单例模式的装饰器"""
    def __init__(self, cls):
        self.cls = cls
        self.instance = None

    def __call__(self, *args, **kwargs):
        if self.instance is None:
            self.instance = self.cls(*args, **kwargs)
        return self.instance

@Singleton
class Database:
    def __init__(self):
        print("初始化数据库连接...")

db1 = Database()  # 初始化数据库连接...
db2 = Database()  # (无输出，返回同一实例)
print(db1 is db2) # True
```

---

## 2.5 上下文管理器 (Context Manager)

`with` 语句确保资源在使用后被**自动释放**，即使发生异常也不例外。

### 基本原理

```python
# with 语句等价于：
# f = open("file.txt")
# try:
#     data = f.read()
# finally:
#     f.close()

with open("file.txt", "w") as f:
    f.write("Hello")
# 自动调用 f.close()，即使中途异常也会执行
```

### 自定义上下文管理器

```python
class Timer:
    """计时器上下文管理器"""
    def __enter__(self):
        self.start = time.perf_counter()
        return self  # 返回值赋给 as 后的变量

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.elapsed = time.perf_counter() - self.start
        print(f"耗时: {self.elapsed:.6f}s")
        # 返回 True 可抑制异常（通常不这么做）
        return False

with Timer() as t:
    sum(range(10**7))
# 耗时: 0.xxxxxxs
```

### contextlib 简化

```python
from contextlib import contextmanager

@contextmanager
def timer():
    """用生成器创建上下文管理器"""
    start = time.perf_counter()
    try:
        yield  # 在此处执行 with 块内的代码
    finally:
        elapsed = time.perf_counter() - start
        print(f"耗时: {elapsed:.6f}s")

with timer():
    sum(range(10**7))
```

### 实战：临时切换目录

```python
import os
from contextlib import contextmanager

@contextmanager
def chdir(path):
    old = os.getcwd()
    os.chdir(path)
    try:
        yield
    finally:
        os.chdir(old)  # 保证恢复原目录

with chdir("/tmp"):
    print(os.getcwd())  # /tmp
print(os.getcwd())      # 恢复原目录
```

---

## 2.6 Lambda 与高阶函数

### lambda 表达式

> `lambda 参数: 返回值` — 一行匿名函数。

```python
# 排序 key
students = [("Alice", 85), ("Bob", 92), ("Charlie", 78)]
students.sort(key=lambda x: x[1])       # 按分数升序
students.sort(key=lambda x: x[1], reverse=True)  # 降序

# 一次性回调
nums = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, nums))
# [1, 4, 9, 16, 25]
```

### map / filter / reduce

```python
# map — 对每个元素应用函数
nums = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, nums))
# [2, 4, 6, 8, 10]

# filter — 按条件筛选
evens = list(filter(lambda x: x % 2 == 0, nums))
# [2, 4]

# reduce — 累积计算
from functools import reduce
product = reduce(lambda a, b: a * b, nums)  # 120 (1*2*3*4*5)
total = reduce(lambda a, b: a + b, nums)    # 15
```

> [!tip] 推导式 vs map/filter
> 多数情况下**推导式更 Pythonic**：
> ```python
> [x*2 for x in nums]           # 优于 map(lambda x: x*2, nums)
> [x for x in nums if x%2==0]   # 优于 filter(lambda x: x%2==0, nums)
> ```

### sorted 的 key 参数

```python
# 按字符串长度排序
words = ["python", "go", "javascript", "c"]
sorted(words, key=len)  # ['c', 'go', 'python', 'javascript']

# 按字典某字段排序
records = [{"name": "A", "age": 30}, {"name": "B", "age": 25}]
sorted(records, key=lambda r: r["age"])

# 多级排序：先按成绩降序，再按姓名升序
students = [("Bob", 92), ("Alice", 92), ("Charlie", 85)]
sorted(students, key=lambda x: (-x[1], x[0]))
```

---

## 2.7 面向对象高级特性

### @property — 属性访问控制

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        """getter — 像属性一样访问"""
        return self._radius

    @radius.setter
    def radius(self, value):
        """setter — 带验证"""
        if value <= 0:
            raise ValueError("半径必须为正数")
        self._radius = value

    @property
    def area(self):
        """只读计算属性"""
        return 3.14159 * self._radius ** 2

c = Circle(5)
print(c.radius)   # 5       — 像属性一样访问
print(c.area)     # 78.53975
c.radius = 10     # 触发 setter 验证
# c.area = 100    # AttributeError: can't set attribute
```

### 类方法与静态方法

```python
class Date:
    def __init__(self, year, month, day):
        self.year, self.month, self.day = year, month, day

    @classmethod
    def from_string(cls, date_str):
        """类方法：cls 是类本身，常用于替代构造器"""
        year, month, day = map(int, date_str.split("-"))
        return cls(year, month, day)

    @staticmethod
    def is_valid_date(year, month, day):
        """静态方法：不需要访问类或实例，纯工具函数"""
        return 1 <= month <= 12 and 1 <= day <= 31

d1 = Date(2024, 1, 15)
d2 = Date.from_string("2024-01-15")  # 替代构造器
print(Date.is_valid_date(2024, 2, 30))  # False
```

### `__slots__` — 内存优化

```python
class Point:
    __slots__ = ("x", "y")  # 禁止动态添加属性，节省内存

    def __init__(self, x, y):
        self.x = x
        self.y = y

p = Point(1, 2)
# p.z = 3  # AttributeError: 'Point' object has no attribute 'z'
```

> 当需要创建**数百万个小对象**时，`__slots__` 可显著减少内存占用。

### dataclass — 数据容器

```python
from dataclasses import dataclass, field

@dataclass
class ImageConfig:
    width: int = 224
    height: int = 224
    channels: int = 3
    mean: tuple = (0.485, 0.456, 0.406)
    std: tuple = (0.229, 0.224, 0.225)

cfg = ImageConfig()
cfg2 = ImageConfig(width=512, height=512)
print(cfg)       # ImageConfig(width=224, height=224, ...) 自动生成 __repr__
print(cfg == cfg2)  # False — 自动生成 __eq__

# 可变默认值需用 field
@dataclass
class Batch:
    data: list = field(default_factory=list)  # 每次创建新列表
```

### 常用魔术方法

```python
class Vector:
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __repr__(self):
        """给开发者看的字符串（调试用）"""
        return f"Vector({self.x}, {self.y})"

    def __str__(self):
        """给用户看的字符串"""
        return f"({self.x}, {self.y})"

    def __add__(self, other):
        """运算符重载：+"""
        return Vector(self.x + other.x, self.y + other.y)

    def __eq__(self, other):
        """运算符重载：=="""
        return self.x == other.x and self.y == other.y

    def __len__(self):
        """len() 行为"""
        return 2

    def __getitem__(self, index):
        """索引访问 v[0]"""
        return self.x if index == 0 else self.y

    def __call__(self):
        """让实例可被调用"""
        return (self.x**2 + self.y**2) ** 0.5

v1 = Vector(3, 4)
v2 = Vector(1, 2)
print(v1 + v2)     # Vector(4, 6)
print(v1[0])       # 3
print(v1())        # 5.0 — 调用了 __call__，返回模长
```

> [!summary] 魔术方法速查
> | 方法 | 触发方式 |
> |------|----------|
> | `__init__` | `obj = Class()` |
> | `__str__` | `print(obj)`, `str(obj)` |
> | `__repr__` | `repr(obj)`, 交互式直接输入 obj |
> | `__len__` | `len(obj)` |
> | `__getitem__` | `obj[key]` |
> | `__setitem__` | `obj[key] = value` |
> | `__iter__` | `for x in obj` |
> | `__call__` | `obj()` |
> | `__enter__/__exit__` | `with obj:` |

---

## 2.8 类型注解 (Type Hints)

> Python 3.5+ 支持类型注解，提升代码可读性和 IDE 智能提示。

### 基本注解

```python
def greet(name: str, age: int) -> str:
    return f"{name} is {age} years old"

# 变量注解
count: int = 0
names: list[str] = ["Alice", "Bob"]
scores: dict[str, float] = {"math": 95.5, "english": 88.0}

# 复合类型
from typing import Optional, Union, List, Dict, Tuple, Callable

def find_user(id: int) -> Optional[dict]:
    """可能返回 None"""
    ...

def process(data: Union[str, bytes]) -> str:
    """接受 str 或 bytes"""
    ...

# 可调用对象
def apply(func: Callable[[int, int], int], a: int, b: int) -> int:
    """func 接受两个 int，返回一个 int"""
    return func(a, b)
```

### 泛型与 Protocol

```python
from typing import TypeVar, Protocol

T = TypeVar("T")

def first(items: list[T]) -> T:
    """泛型函数：输入 list[T]，输出 T"""
    return items[0]

num = first([1, 2, 3])     # num 类型推断为 int
s = first(["a", "b", "c"]) # s 类型推断为 str

# Protocol — 结构化子类型（鸭子类型）
class SupportsClose(Protocol):
    def close(self) -> None: ...

def cleanup(resource: SupportsClose) -> None:
    resource.close()
```

---

## 2.9 并发编程概览

> Python 三种并发模型对比：

|     | 模型                  | 适用场景               | 是否受 GIL 限制 | 特点        |
| --- | ------------------- | ------------------ | :--------: | --------- |
|     | **threading**       | I/O 密集型（网络请求、文件读写） |     是      | 轻量，共享内存   |
|     | **multiprocessing** | CPU 密集型（计算、图像处理）   |     否      | 独立进程，真正并行 |
|     | **asyncio**         | 高并发 I/O（Web 服务、爬虫） |     是      | 单线程协程，最轻量 |

```python
# threading — I/O 密集型
import threading

def download(url):
    print(f"下载 {url}...")
    # requests.get(url) ...

threads = [threading.Thread(target=download, args=(url,))
           for url in urls]
for t in threads: t.start()
for t in threads: t.join()

# multiprocessing — CPU 密集型（图像处理等）
from multiprocessing import Pool

def process_image(path):
    # 读取、处理、保存图片
    ...

with Pool(processes=4) as pool:
    pool.map(process_image, image_paths)

# asyncio — 高并发 I/O
import asyncio

async def fetch(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as resp:
            return await resp.text()

async def main():
    tasks = [fetch(url) for url in urls]
    results = await asyncio.gather(*tasks)

asyncio.run(main())
```

> [!warning] GIL 注意
> Python 的 GIL（全局解释器锁）使得同一时刻**只有一个线程**执行 Python 字节码。CPU 密集型任务请用 `multiprocessing` 或 C 扩展。

---

## 2.10 实用标准库

### functools

```python
from functools import lru_cache, partial, wraps, reduce

# lru_cache — 函数结果缓存（见 2.4 装饰器章节）

# partial — 偏函数（固定部分参数）
def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
cube = partial(power, exp=3)
print(square(5))  # 25
print(cube(5))    # 125

# wraps — 保留装饰函数的元信息（见 2.4 装饰器章节）
```

### itertools

```python
import itertools

# 无限迭代器
count = itertools.count(10, 2)    # 10, 12, 14, ...
cycle = itertools.cycle("AB")     # A, B, A, B, ...
repeat = itertools.repeat("Hi", 3) # Hi, Hi, Hi

# 组合迭代器
print(list(itertools.product("AB", "12")))
# [('A', '1'), ('A', '2'), ('B', '1'), ('B', '2')]

print(list(itertools.permutations("ABC", 2)))
# [('A','B'), ('A','C'), ('B','A'), ('B','C'), ('C','A'), ('C','B')]

print(list(itertools.combinations("ABC", 2)))
# [('A','B'), ('A','C'), ('B','C')]

# chain — 串联多个可迭代对象
print(list(itertools.chain([1, 2], [3, 4], [5, 6])))
# [1, 2, 3, 4, 5, 6]

# groupby — 按 key 分组（注意：需先排序）
data = [("A", 1), ("A", 2), ("B", 3), ("B", 4)]
for key, group in itertools.groupby(data, key=lambda x: x[0]):
    print(key, list(group))
# A [('A', 1), ('A', 2)]
# B [('B', 3), ('B', 4)]
```

### collections

```python
from collections import defaultdict, Counter, deque, namedtuple, OrderedDict

# defaultdict — 带默认值的字典
dd = defaultdict(list)
dd["fruits"].append("apple")
dd["fruits"].append("banana")
print(dd["fruits"])   # ['apple', 'banana']
print(dd["unknown"])  # [] — 不会 KeyError

# Counter — 计数器
text = "abracadabra"
c = Counter(text)
print(c)              # Counter({'a': 5, 'b': 2, 'r': 2, ...})
print(c.most_common(2))  # [('a', 5), ('b', 2)]

# deque — 双端队列（两端 O(1) 操作）
dq = deque([1, 2, 3])
dq.appendleft(0)      # [0, 1, 2, 3]
dq.append(4)          # [0, 1, 2, 3, 4]
dq.popleft()          # 0
dq.pop()              # 4

# namedtuple — 具名元组
Point = namedtuple("Point", ["x", "y"])
p = Point(3, 4)
print(p.x, p.y)  # 3 4
print(p[0])      # 3 — 仍支持索引
```

---

## 2.11 NumPy 核心用法

> NumPy 是机器视觉数据处理的基础，掌握其核心用法至关重要。

### ndarray 创建与属性

```python
import numpy as np

# 创建数组
a = np.array([1, 2, 3])
b = np.zeros((3, 4), dtype=np.float32)
c = np.ones((2, 2))
d = np.arange(10)           # [0 1 2 ... 9]
e = np.linspace(0, 1, 5)   # [0.   0.25 0.5  0.75 1.  ]
f = np.random.randn(3, 3)  # 标准正态分布

# 属性
print(a.shape)     # (3,)    维度
print(b.dtype)     # float32 数据类型
print(b.ndim)      # 2       维数
print(b.size)      # 12      元素总数
print(b.nbytes)    # 48      内存占用(bytes)
```

### 花式索引与布尔索引

```python
arr = np.arange(12).reshape(3, 4)

# 花式索引 — 用整数数组索引
print(arr[[0, 2]])        # 第0行和第2行
print(arr[[0, 2], [1, 3]])  # (0,1) 和 (2,3) 两个元素 → [1, 11]

# 布尔索引 — 条件筛选
print(arr[arr > 5])       # [6 7 8 9 10 11]
arr[arr > 5] = 0          # 条件赋值

# 实战：筛选满足条件的像素
image = np.random.randint(0, 256, (100, 100, 3), dtype=np.uint8)
mask = image[:, :, 0] > 128  # R 通道 > 128
red_pixels = image[mask]     # 所有偏红像素
```

### 广播机制 (Broadcasting)

> 不同形状的数组在运算时自动"广播"到相同形状。

```python
# 标量广播
arr = np.array([1, 2, 3])
print(arr + 10)  # [11 12 13]

# 行向量 + 列向量
row = np.array([[1, 2, 3]])    # shape (1, 3)
col = np.array([[1], [2]])     # shape (2, 1)
print(row + col)
# [[2 3 4]
#  [3 4 5]]  → shape (2, 3)

# 广播规则：(3, 4, 2) + (4, 2) → 从右对齐，维度为1的扩展
# None / np.newaxis 手动添加维度
a = np.array([1, 2, 3])         # shape (3,)
b = np.array([[1], [2], [3]])   # shape (3, 1)
print(a + b)
# [[2 3 4]
#  [3 4 5]
#  [4 5 6]]
```

### 常用聚合与变换

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

# 聚合
print(arr.sum())      # 21
print(arr.mean())     # 3.5
print(arr.std())      # 标准差
print(arr.min(axis=0))  # [1 2 3]  每列最小
print(arr.max(axis=1))  # [3 6]    每行最大

# 变换
arr.T             # 转置
arr.reshape(3, 2) # 变形
arr.flatten()     # 展平 → [1 2 3 4 5 6]
np.concatenate([arr, arr], axis=0)  # 拼接
np.stack([arr, arr], axis=0)        # 堆叠（新增维度）

# where — 向量化 if-else
x = np.array([1, 2, 3, 4, 5])
result = np.where(x > 3, x * 10, x)
# [1, 2, 3, 40, 50]
```

---

# 三、常见问题与陷阱

## 3.1 可变默认参数

```python
# ❌ 错误：默认参数只在函数定义时计算一次
def add_item(item, lst=[]):
    lst.append(item)
    return lst

print(add_item(1))  # [1]
print(add_item(2))  # [1, 2] — 意外！lst 是同一个对象

# ✅ 正确做法
def add_item(item, lst=None):
    if lst is None:
        lst = []
    lst.append(item)
    return lst
```

## 3.2 浅拷贝 vs 深拷贝

```python
import copy

original = [[1, 2], [3, 4]]
shallow = original[:]           # 或 copy.copy(original)
deep = copy.deepcopy(original)

original[0][0] = 99
print(shallow)  # [[99, 2], [3, 4]] — 内层列表是共享的！
print(deep)     # [[1, 2], [3, 4]]  — 完全独立

# 特别注意：NumPy 切片是视图（浅拷贝）
# slice_copy = arr[:2, :2].copy()  # 需要显式 .copy()
```

## 3.3 GIL 与性能

- **GIL（全局解释器锁）**：Python 字节码同一时刻仅一个线程执行
- **I/O 密集型**：`threading` 足够（I/O 操作会释放 GIL）
- **CPU 密集型**：必须用 `multiprocessing` 或 C 扩展（如 NumPy 内部已释放 GIL）
- **大规模并发 I/O**：`asyncio` 性能最优

## 3.4 循环中修改列表

```python
# ❌ 边遍历边删除 — 索引错乱
lst = [1, 2, 3, 4, 5]
for i in range(len(lst)):
    if lst[i] % 2 == 0:
        del lst[i]  # 索引已变！

# ✅ 方法1：倒序遍历
for i in range(len(lst) - 1, -1, -1):
    if lst[i] % 2 == 0:
        del lst[i]

# ✅ 方法2：新建列表（最推荐）
lst = [x for x in lst if x % 2 != 0]
```

---

# 附录：速查表

## A. 常用内置函数

|     | 函数                        | 用途        | 示例                                             |
| --- | ------------------------- | --------- | ---------------------------------------------- |
|     | `len(x)`                  | 长度        | `len([1,2,3])` → 3                             |
|     | `range(n)`                | 整数序列      | `list(range(3))` → [0,1,2]                     |
|     | `enumerate(seq)`          | 索引+值      | `for i, v in enumerate(lst)`                   |
|     | `zip(a, b)`               | 并行迭代      | `list(zip("AB","12"))` → [('A','1'),('B','2')] |
|     | `type(x)`                 | 类型        | `type(42)` → int                               |
|     | `isinstance(x, t)`        | 类型检查      | `isinstance(42, int)` → True                   |
|     | `any(seq)` / `all(seq)`   | 任一/全部为真   | `any([False,True])` → True                     |
|     | `sorted(seq, key=...)`    | 排序（返回新列表） | `sorted([3,1,2])` → [1,2,3]                    |
|     | `reversed(seq)`           | 反转迭代器     | `list(reversed([1,2,3]))`                      |
|     | `open(path, mode)`        | 打开文件      | `open("f.txt", "r")`                           |
|     | `hasattr(obj, name)`      | 检查属性      | `hasattr([], "append")`                        |
|     | `getattr(obj, name)`      | 获取属性      | `getattr(obj, "x", 0)`                         |
|     | `setattr(obj, name, val)` | 设置属性      | `setattr(obj, "x", 10)`                        |
|     | `eval(s)` / `exec(s)`     | 执行字符串     | 慎用！                                            |

## B. pip 常用命令

```bash
pip install package           # 安装包
pip install package==1.0.0    # 安装指定版本
pip uninstall package         # 卸载
pip list                      # 列出已安装
pip show package              # 查看包详情
pip freeze > requirements.txt # 导出依赖
pip install -r requirements.txt # 从文件安装
pip install --upgrade package # 升级包
```

## C. 虚拟环境

```bash
# 创建虚拟环境
python -m venv venv

# 激活（Windows）
venv\Scripts\activate
# 激活（Linux/macOS）
source venv/bin/activate

# 退出
deactivate
```

---

> [!info] 关联笔记
> - [[机器视觉]] — 机器视觉基础知识
> - [[OpenCV笔记]] — 图像处理实战（NumPy 是 OpenCV 的基石）
> - [[深度学习笔记]] — 深度学习理论与框架
