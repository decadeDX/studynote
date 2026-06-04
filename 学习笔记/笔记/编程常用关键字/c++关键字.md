[[编程常用关键字]]
1. explicit 关键字 （翻译：直白的、明确的）
作用：禁止单参数构造函数的隐式类型转换
示例：
```c++
class A {
public:
    explicit A(int x) {} // 加了 explicit
};

A a1(10);   // 正常调用构造函数 ✅
A a2 = 10;  // 报错！禁止隐式转换 ❌
```
去掉 explicit 时，`A a2 = 10;` 会自动把 int 转成 A 对象，容易出 bug，所以常用 `explicit` 限制。