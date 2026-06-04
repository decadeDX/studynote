

# 高级特性
## 切片
[start:stop:step]
其中 **stop 是“切到不取”的右边界**（和数学里的左闭右开区间类似）。
- **正索引**从左数 `0, 1, 2, …`；**负索引**从右数 `-1, -2, …`。
- **省略** start 表示从开头；**省略** stop 表示到末尾。`[:]` 常用来**浅拷贝**一层列表；`[::-1]` 表示**整段反转**。

 
```python
list1 = [1,2,3,4,5,6,7,8,9,10]     
print(list1[1:5]) #1,2,3,4,5     
print(list1[5:])     
print(list1[:5])     
print(list1[::2])     
print(list1[1::2])     
print(list1[::-1])     
print(list1[-1:-5:-1])     
print()
```


![[计算机图片基础知识.png]]

1. 人工智能方向最流行的两款web ui框架：
	1. Streamlit
	2. Gradio 是一个 Python Web UI 框架，主要用于快速搭建演示页面
2. vue html页面的web ui框架：
	1. ElementUI
	2. Ant Design