---
tags:
  - JavaScript
  - 前端
updated: 2026-07-01
---

# JavaScript 笔记

> JavaScript 是一种轻量级的解释型编程语言，主要用于 Web 开发，也可用于服务端（Node.js）。

---

## 基础语法

### 变量声明

|     | 关键字    | 作用域   | 可重复声明 | 可重新赋值 | 暂时性死区 |
| :-: | :-------- | :------- | :--------: | :--------: | :--------: |
|     | `var`     | 函数级   |     ✅     |     ✅     |     ❌     |
|     | `let`     | 块级     |     ❌     |     ✅     |     ✅     |
|     | `const`   | 块级     |     ❌     |     ❌     |     ✅     |

> **建议**：默认使用 `const`，只在需要重新赋值时用 `let`，避免使用 `var`。

### 数据类型

- **基本类型**：`string`、`number`、`boolean`、`null`、`undefined`、`symbol`、`bigint`
- **引用类型**：`object`（含 `array`、`function`、`date` 等）

**类型检测**：
```javascript
typeof "hello"      // "string"
typeof 42           // "number"
typeof true         // "boolean"
typeof null         // "object" (JS 历史遗留 bug)
typeof undefined    // "undefined"
typeof [1,2,3]      // "object"
Array.isArray([1])  // true
```

### 类型转换

|     | 方式             | 示例                    | 结果       |
| :-: | :--------------- | :---------------------- | :--------- |
|     | **显式转字符串** | `String(123)`           | `"123"`    |
|     | **显式转数字**   | `Number("123")`         | `123`      |
|     | **转布尔**       | `Boolean(0)`            | `false`    |
|     | **快速转字符串** | `123 + ''`              | `"123"`    |
|     | **快速转数字**   | `+"123"` 或 `'123'-0`  | `123`      |
|     | **转整数**       | `parseInt("12.34")`     | `12`       |
|     | **转浮点**       | `parseFloat("12.34")`   | `12.34`    |

**假值列表**：
```javascript
false、0、-0、0n、""、null、undefined、NaN
```

---

## 运算符

|     | 类别         | 运算符                                            |
| :-: | :----------- | :------------------------------------------------ |
|     | **算术**     | `+` `-` `*` `/` `%` `**` `++` `--`               |
|     | **比较**     | `>` `<` `>=` `<=` `==` `===` `!=` `!==`          |
|     | **逻辑**     | `&&` `\|\|` `!` `??`（空值合并）                   |
|     | **赋值**     | `=` `+=` `-=` `*=` `/=`                          |
|     | **可选链**   | `?.`（避免 `Cannot read property of undefined`）  |

> **`==` vs `===`**：`===` 严格相等（不转换类型），`==` 会做类型转换。始终使用 `===`。

> **`??` vs `\|\|`**：`??` 只在值为 `null`/`undefined` 时取右侧；`\|\|` 在值为任何假值时取右侧。

---

## 控制流与循环

### 条件判断

```javascript
// if-else
if (condition) { ... }
else if (condition) { ... }
else { ... }

// switch
switch (val) {
  case 'a': ...; break;
  default: ...
}

// 三元运算符
const result = condition ? 'A' : 'B';
```

### 循环

|     | 方式            | 适用场景                   |
| :-: | :-------------- | :------------------------- |
|     | `for`           | 已知循环次数               |
|     | `for...of`      | 遍历可迭代对象（数组、Map、Set） |
|     | `for...in`      | 遍历对象**键名**（慎用于数组）  |
|     | `while`         | 条件型循环                 |
|     | `do...while`    | 至少执行一次               |
|     | `forEach()`     | 数组遍历（不可 break）      |

```javascript
// for...of 遍历数组
for (const item of arr) { ... }

// for...in 遍历对象
for (const key in obj) {
  if (obj.hasOwnProperty(key)) { ... }
}
```

---

## 函数

### 函数定义

```javascript
// 函数声明（提升）
function add(a, b) { return a + b; }

// 函数表达式（不提升）
const add = function(a, b) { return a + b; };

// 箭头函数（无自己的 this/arguments）
const add = (a, b) => a + b;
const square = x => x * x;
```

### 箭头函数特性

- 不绑定 `this`（继承外层作用域的 `this`）
- 没有 `arguments` 对象（可用剩余参数 `...args` 代替）
- 不能作为构造函数（不能用 `new`）
- 不能使用 `yield`

### 闭包 (Closure)

```javascript
function createCounter() {
  let count = 0;
  return function() {
    return ++count;
  };
}
const counter = createCounter();
counter(); // 1
counter(); // 2
```

> **闭包**：函数 + 其创建时所在作用域的捆绑，使内部函数可以访问外部函数的变量。

### 剩余参数与展开运算符

```javascript
// 剩余参数
function sum(...nums) { return nums.reduce((a,b) => a + b); }

// 展开运算符
const arr1 = [1,2], arr2 = [...arr1, 3, 4];  // [1,2,3,4]
const obj1 = {a:1}, obj2 = {...obj1, b:2};   // {a:1, b:2}
```

---

## 对象

### 创建与操作

```javascript
// 字面量
const obj = { name: 'Alice', age: 25 };

// 属性简写
const name = 'Alice';
const obj = { name };  // { name: 'Alice' }

// 计算属性名
const key = 'color';
const obj = { [key]: 'red' };

// 删除属性
delete obj.age;

// 检查属性
'name' in obj;         // true
obj.hasOwnProperty('name');  // true
```

### 常用方法

|     | 方法                          | 作用                   |
| :-: | :---------------------------- | :--------------------- |
|     | `Object.keys(obj)`            | 获取所有键             |
|     | `Object.values(obj)`          | 获取所有值             |
|     | `Object.entries(obj)`         | 获取键值对数组         |
|     | `Object.assign(target, src)`  | 合并对象               |
|     | `Object.freeze(obj)`          | 冻结对象（不可变）      |
|     | `Object.seal(obj)`            | 密封对象（不可增删可改） |

---

## 数组

### 创建与检测

```javascript
const arr = [1, 2, 3];
const arr2 = new Array(5);     // 长度为 5 的空数组
const arr3 = Array.from('abc'); // ['a','b','c']
const arr4 = Array.of(1, 2, 3); // [1,2,3]
Array.isArray(arr);             // true
```

### 核心方法

**增删改**：

|     | 方法                    | 作用                 | 是否修改原数组 |
| :-: | :---------------------- | :------------------- | :----------: |
|     | `push(val)`             | 末尾添加             |     ✅      |
|     | `pop()`                 | 移除末尾             |     ✅      |
|     | `unshift(val)`          | 开头添加             |     ✅      |
|     | `shift()`               | 移除开头             |     ✅      |
|     | `splice(idx, n, ...)`   | 删除/插入/替换        |     ✅      |
|     | `slice(start, end)`     | 截取（浅拷贝）         |     ❌      |
|     | `concat(arr)`           | 合并                 |     ❌      |

**遍历与转换**：

```javascript
arr.forEach((item, idx) => { ... });        // 遍历
const newArr = arr.map((x) => x * 2);        // 映射
const filtered = arr.filter((x) => x > 0);   // 过滤
const found = arr.find((x) => x > 0);        // 查找第一个
const hasItem = arr.some((x) => x > 0);      // 是否有满足条件的
const allMatch = arr.every((x) => x > 0);    // 是否全部满足
const sum = arr.reduce((acc, x) => acc + x, 0); // 归约
const sorted = arr.sort((a,b) => a - b);     // 排序（修改原数组）
```

> **`map` vs `forEach`**：`map` 返回新数组，`forEach` 仅遍历。要转换数据用 `map`。

---

## ES6+ 现代特性

### 解构赋值

```javascript
// 数组解构
const [a, b, ...rest] = [1, 2, 3, 4];  // a=1, b=2, rest=[3,4]

// 对象解构
const { name, age = 18 } = { name: 'Alice' };
const { name: userName } = { name: 'Alice' };  // 重命名

// 函数参数解构
function print({ name, age }) { ... }
```

### 模板字符串

```javascript
const name = 'World';
const greeting = `Hello, ${name}!`;  // "Hello, World!"

// 多行字符串
const multi = `
  Line 1
  Line 2
`;
```

### Promise 与异步

```javascript
// 创建 Promise
const p = new Promise((resolve, reject) => {
  setTimeout(() => resolve('done'), 1000);
});

// 链式调用
p.then(result => { ... })
 .catch(err => { ... })
 .finally(() => { ... });
```

### async/await

```javascript
async function fetchData() {
  try {
    const res = await fetch(url);
    const data = await res.json();
    return data;
  } catch (err) {
    console.error(err);
  }
}
```

### Promise 静态方法

|     | 方法                              | 作用                          |
| :-: | :-------------------------------- | :---------------------------- |
|     | `Promise.all([...])`              | 全部成功才 resolve，一错即 reject |
|     | `Promise.allSettled([...])`       | 等待全部完成（无论成功/失败）    |
|     | `Promise.race([...])`             | 返回最先完成的（首个结果）       |
|     | `Promise.any([...])`              | 返回首个成功 resolve 的         |
|     | `Promise.resolve(val)`            | 返回一个 resolved 的 Promise    |

---

## 原型与类

### 原型链

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.sayHi = function() {
  console.log(`Hi, I'm ${this.name}`);
};

const p = new Person('Alice');
p.sayHi();
// p → Person.prototype → Object.prototype → null
```

### ES6 Class 语法

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  sayHi() {
    console.log(`Hi, I'm ${this.name}`);
  }

  static create(name) {     // 静态方法
    return new Person(name);
  }
}

// 继承
class Student extends Person {
  constructor(name, grade) {
    super(name);            // 必须调用 super()
    this.grade = grade;
  }
}
```

---

## 常用 API

### 字符串

|     | 方法                              | 作用               |
| :-: | :-------------------------------- | :----------------- |
|     | `str.includes(sub)`               | 是否包含           |
|     | `str.startsWith(sub)`             | 是否以某字符串开头 |
|     | `str.endsWith(sub)`               | 是否以某字符串结尾 |
|     | `str.trim()`                      | 去除首尾空格       |
|     | `str.split(sep)`                  | 分割为数组         |
|     | `str.replace(old, new)`           | 替换               |
|     | `str.repeat(n)`                   | 重复 n 次          |

### 数字与 Math

|     | 方法/属性           | 作用                 |
| :-: | :------------------ | :------------------- |
|     | `Math.round(x)`     | 四舍五入             |
|     | `Math.floor(x)`     | 向下取整             |
|     | `Math.ceil(x)`      | 向上取整             |
|     | `Math.random()`     | 返回 [0,1) 随机数    |
|     | `Math.max(...nums)` | 最大值               |
|     | `Math.min(...nums)` | 最小值               |
|     | `Number.isNaN(x)`   | 判断是否为 NaN       |
|     | `Number.isFinite(x)`| 判断是否为有限数     |

### Set 与 Map

```javascript
// Set（唯一值集合）
const set = new Set([1,2,3,3,2]);  // {1,2,3}
set.add(4).delete(1);
set.has(2);    // true
set.size;      // 3

// Map（键值对，键可为任意类型）
const map = new Map();
map.set('key', 'value');
map.get('key');       // "value"
map.has('key');       // true
map.delete('key');
map.forEach((v,k) => { ... });
```

---

## 常见陷阱

|     | 陷阱               | 说明                                           | 解决方案                 |
| :-: | :----------------- | :--------------------------------------------- | :----------------------- |
|     | `this` 丢失        | 回调函数中 `this` 指向改变                      | 箭头函数 / `.bind()`     |
|     | 浮点精度           | `0.1 + 0.2 !== 0.3`                            | 使用 `toFixed()` 或库    |
|     | `==` 类型转换      | `0 == '0'` 为 `true`                           | 始终使用 `===`           |
|     | NaN 不等于自身     | `NaN === NaN` 为 `false`                        | 使用 `Number.isNaN()`   |
|     | 引用类型比较       | `{} === {}` 为 `false`（比较引用而非值）         | 深比较或用 JSON 序列化  |
|     | `sort()` 默认比较  | `[1,10,2].sort()` → `[1,10,2]`（按字符串排）    | `sort((a,b) => a - b)`  |

---

## 相关笔记

- [[java学习/java基础]] — Java 基础对比
- [[数据结构]] — 数据结构相关
- [[编程常用关键字/编程常用关键字]] — 各语言关键字对比
