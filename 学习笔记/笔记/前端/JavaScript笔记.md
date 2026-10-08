---
tags:
  - JavaScript
  - 前端
updated: 2026-07-16
---

# JavaScript 笔记

> JavaScript 是一种轻量级的解释型编程语言，主要用于 Web 开发，也可用于服务端（Node.js）。

---

## 基础语法

### 变量声明

|     | 关键字     | 作用域 | 可重复声明 | 可重新赋值 | 暂时性死区 |
| :-: | :------ | :-- | :---: | :---: | :---: |
|     | `var`   | 函数级 |   ✅   |   ✅   |   ❌   |
|     | `let`   | 块级  |   ❌   |   ✅   |   ✅   |
|     | `const` | 块级  |   ❌   |   ❌   |   ✅   |

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

|     | 类别      | 运算符                                          |     |
| :-: | :------ | :------------------------------------------- | --- |
|     | **算术**  | `+` `-` `*` `/` `%` `**` `++` `--`           |     |
|     | **比较**  | `>` `<` `>=` `<=` `==``===``!=` `!==`        |     |
|     | **逻辑**  | `&&` `\|\|` `!` `??`（空值合并）                   |     |
|     | **赋值**  | `=` `+=` `-=` `*=` `/=`                      |     |
|     | **可选链** | `?.`（避免 `Cannot read property of undefined`） |     |
          

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

## DOM 操作

> **DOM (Document Object Model)**：浏览器将 HTML 文档解析为树状结构，提供 JavaScript 操作页面元素的接口。

### 选择元素

|     | 方法                               | 说明                       |
| :-: | :--------------------------------- | :------------------------- |
|     | `document.querySelector(selector)` | 返回匹配的第一个元素         |
|     | `document.querySelectorAll(sel)`   | 返回所有匹配元素（NodeList） |
|     | `document.getElementById(id)`      | 通过 ID 获取元素             |
|     | `document.getElementsByClassName(c)`| 通过类名获取（HTMLCollection）|
|     | `document.getElementsByTagName(t)` | 通过标签获取（HTMLCollection）|

> **`querySelector`** 是最灵活的方式，支持任意 CSS 选择器，推荐优先使用。

### DOM 遍历

|     | 属性/方法                             | 说明                |
| :-: | :---------------------------------- | :----------------- |
|     | `el.parentElement`                  | 父元素              |
|     | `el.children`                       | 子元素集合           |
|     | `el.firstElementChild`              | 第一个子元素          |
|     | `el.lastElementChild`               | 最后一个子元素         |
|     | `el.nextElementSibling`             | 下一个兄弟元素        |
|     | `el.previousElementSibling`         | 上一个兄弟元素        |
|     | `el.closest(selector)`              | 向上匹配最近的祖先元素   |

### 操作内容与属性

|     | 属性/方法                                   | 说明                |
| :-: | :------------------------------------------ | :----------------- |
|     | `el.textContent`                            | 获取/设置文本内容（安全） |
|     | `el.innerHTML`                              | 获取/设置 HTML（XSS 风险）|
|     | `el.getAttribute(name)`                     | 获取属性值           |
|     | `el.setAttribute(name, value)`              | 设置属性值           |
|     | `el.removeAttribute(name)`                  | 移除属性             |
|     | `el.classList.add/remove/toggle/contains(c)` | 操作 CSS 类名        |
|     | `el.style.property`                         | 操作行内样式          |
|     | `el.dataset.key`                            | 访问 `data-*` 自定义属性 |

```javascript
// classList 操作
el.classList.add('active');
el.classList.remove('hidden');
el.classList.toggle('dark-mode');
el.classList.contains('active');  // true/false

// data-* 属性
// <div data-user-id="123"></div>
el.dataset.userId;  // "123"
```

### 创建与删除元素

|     | 方法                                   | 说明                |
| :-: | :------------------------------------- | :----------------- |
|     | `document.createElement(tag)`          | 创建元素             |
|     | `el.append(node)`                      | 末尾添加（支持多个）    |
|     | `el.appendChild(node)`                 | 末尾添加（单个）       |
|     | `el.prepend(node)`                     | 开头添加             |
|     | `el.insertBefore(new, ref)`            | 插入到 ref 前        |
|     | `el.removeChild(node)`                 | 移除子元素           |
|     | `el.remove()`                          | 移除自身             |
|     | `el.replaceChild(new, old)`            | 替换子元素           |
|     | `el.cloneNode(deep)`                   | 克隆元素（true=深克隆）|

```javascript
// 创建并插入元素
const div = document.createElement('div');
div.textContent = 'Hello';
div.classList.add('card');
document.body.append(div);

// 高级插入 - 相对于某个位置
el.insertAdjacentHTML('beforeend', '<span>text</span>');
// 位置: 'beforebegin' / 'afterbegin' / 'beforeend' / 'afterend'
```

### 事件处理

|     | 方法/属性                               | 说明                |
| :-: | :-------------------------------------- | :----------------- |
|     | `el.addEventListener(type, fn, opts)`    | 绑定事件             |
|     | `el.removeEventListener(type, fn)`       | 移除事件（需同名函数）  |
|     | `el.dispatchEvent(event)`                | 派发自定义事件        |
|     | `event.target`                          | 实际触发事件的元素     |
|     | `event.currentTarget`                    | 绑定事件处理器的元素   |
|     | `event.preventDefault()`                | 阻止默认行为          |
|     | `event.stopPropagation()`               | 阻止事件冒泡          |
|     | `event.stopImmediatePropagation()`       | 阻止冒泡+同级其他监听  |

```javascript
// 绑定事件
el.addEventListener('click', (e) => {
  console.log(e.target, e.currentTarget);
});

// 事件委托：利用冒泡处理动态子元素
parent.addEventListener('click', (e) => {
  if (e.target.matches('.item')) {
    console.log('item clicked:', e.target);
  }
});
```

### 事件流

事件传播分三个阶段：

|     | 阶段       | 说明                     |
| :-: | :--------- | :----------------------- |
|     | **捕获阶段** | 从 `window` 向下传播到目标 |
|     | **目标阶段** | 到达事件目标元素           |
|     | **冒泡阶段** | 从目标向上传播到 `window` |

```javascript
// 第三个参数为 true 时在捕获阶段触发（默认 false 冒泡阶段）
el.addEventListener('click', handler, true);
// 也可传入对象
el.addEventListener('click', handler, { capture: true, once: true });
```

### 常用事件

|     | 事件                 | 说明               |
| :-: | :------------------- | :----------------- |
|     | `click`              | 鼠标点击            |
|     | `dblclick`           | 鼠标双击            |
|     | `mouseenter/leave`   | 鼠标移入/移出（不冒泡） |
|     | `mouseover/out`      | 鼠标移入/移出（会冒泡） |
|     | `mousedown/up`       | 鼠标按下/释放        |
|     | `mousemove`          | 鼠标移动            |
|     | `keydown/keyup`      | 键盘按下/释放        |
|     | `scroll`             | 滚动                |
|     | `submit`             | 表单提交            |
|     | `input`              | 输入框值变化          |
|     | `change`             | 值改变并失去焦点       |
|     | `focus/blur`         | 获得/失去焦点         |
|     | `DOMContentLoaded`   | DOM 树加载完成       |
|     | `load`               | 页面及资源完全加载     |

### 自定义事件

```javascript
// 创建自定义事件
const event = new CustomEvent('userLogin', {
  detail: { userId: 123, name: 'Alice' },
  bubbles: true,       // 是否冒泡
  cancelable: true,    // 是否可取消
});

// 派发事件
el.dispatchEvent(event);

// 监听自定义事件
el.addEventListener('userLogin', (e) => {
  console.log(e.detail); // { userId: 123, name: 'Alice' }
});
```

### 事件监听选项

`addEventListener` 第三个参数可传入配置对象：

|     | 选项        | 说明                                    |
| :-: | :---------- | :-------------------------------------- |
|     | `capture`   | 在捕获阶段触发（默认 `false` 冒泡阶段）     |
|     | `once`      | 自动触发一次后移除（无需手动 `removeEventListener`）|
|     | `passive`   | 声明不调用 `preventDefault()`，提升滚动性能 |
|     | `signal`    | 传入 `AbortSignal`，统一取消多个监听器      |

```javascript
// once：自动一次性监听
el.addEventListener('click', handler, { once: true });

// passive：告诉浏览器不会阻止默认行为（滚动优化）
document.addEventListener('touchstart', handler, { passive: true });

// signal：通过 AbortController 统一取消
const controller = new AbortController();
el.addEventListener('click', handlerA, { signal: controller.signal });
el.addEventListener('mouseenter', handlerB, { signal: controller.signal });
window.addEventListener('resize', handlerC, { signal: controller.signal });

controller.abort(); // 一次性移除所有关联的监听器
```

### 加载事件对比

|     | 事件                  | 触发时机                    | 适用场景            |
| :-: | :-------------------- | :-------------------------- | :----------------- |
|     | `DOMContentLoaded`    | HTML 解析完毕，CSS/图片未加载 | 操作 DOM 元素       |
|     | `load`                | 页面全部资源加载完成          | 获取图片尺寸等       |
|     | `beforeunload`        | 页面即将卸载                 | 提示用户保存数据     |
|     | `unload`              | 页面已卸载                   | 清理工作（慎用）     |

```javascript
// DOMContentLoaded - 最常用的 DOM 就绪事件
document.addEventListener('DOMContentLoaded', () => {
  // 此时可以安全操作 DOM
  document.querySelector('#app').textContent = 'Ready';
});

// beforeunload - 提示用户未保存
window.addEventListener('beforeunload', (e) => {
  e.preventDefault();
  e.returnValue = '';
});
```

### 触摸与指针事件

|     | 事件类型          | 说明                               |
| :-: | :---------------- | :--------------------------------- |
|     | **指针事件 (Pointer)** | 统一鼠标/触摸/笔的现代 API（推荐）    |
|     | `pointerdown/up/move` | 指针按下/释放/移动                   |
|     | `touchstart/move/end` | 触摸专用事件                         |
|     | `wheel`            | 鼠标滚轮                            |

```javascript
// 指针事件 - 同时适配鼠标和触屏
el.addEventListener('pointerdown', (e) => {
  console.log(e.pointerType); // "mouse" | "touch" | "pen"
  console.log(e.clientX, e.clientY);
});
```

---

## 常见陷阱

|     | 陷阱            | 说明                                    | 解决方案                                                                                 |
| :-: | :------------ | :------------------------------------ | :----------------------------------------------------------------------------------- |
|     | `this` 丢失     | 回调函数中 `this` 指向改变                     | 箭头函数 / `.bind()`                                                                     |
|     | 浮点精度          | `0.1 + 0.2 !== 0.3`                   | 使用 `Number.EPSILON` 比较：`Math.abs(a + b - c) < Number.EPSILON`，或使用 decimal.js 等库      |
|     | `==` 类型转换     | `0 == '0'` 为 `true`                   | 始终使用 `===`                                                                           |
|     | NaN 不等于自身     | `NaN === NaN` 为 `false`               | 使用 `Number.isNaN()`                                                                  |
|     | 引用类型比较        | `{} === {}` 为 `false`（比较引用而非值）        | 使用 lodash `_.isEqual()` 或手动递归比较；`JSON.stringify()` 仅限简单结构且有缺陷（不支持 undefined/函数/循环引用） |
|     | `sort()` 默认比较 | `[1,10,2].sort()` → `[1,10,2]`（按字符串排） | `sort((a,b) => a - b)`                                                               |

---

## 相关笔记

- [[java学习/java基础]] — Java 基础对比
- [[数据结构]] — 数据结构相关
- [[编程常用关键字/编程常用关键字]] — 各语言关键字对比
