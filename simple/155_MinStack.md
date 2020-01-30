## 题目：最小栈
设计一个支持 push，pop，top 操作，并能在常数时间内检索到最小元素的栈。

push(x) -- 将元素 x 推入栈中。
pop() -- 删除栈顶的元素。
top() -- 获取栈顶元素。
getMin() -- 检索栈中的最小元素。

## 示例:

MinStack minStack = new MinStack();  
minStack.push(-2);  
minStack.push(0);  
minStack.push(-3);  
minStack.getMin();   --> 返回 -3.  
minStack.pop();  
minStack.top();      --> 返回 0.  
minStack.getMin();   --> 返回 -2.  

## 思路：
```python
# 法一
# 思路： 创建两个栈——数据栈和辅助栈，
# 入栈时：比较已有元素与新来元素，若新来的元素比辅助栈的栈顶元素小，则加入辅助栈；
# 否则，新来的元素比辅助栈的栈顶元素大，则在辅助栈中再添加一次辅助栈的栈顶元素。

class MinStack:

    # 辅助栈和数据栈同步
    # 思路简单不容易出错

    def __init__(self):
        # 初始化两个栈
        # 数据栈
        self.data = []
        # 辅助栈
        self.helper = []

    def push(self, x):
        # 入栈
        self.data.append(x)
        # 如果辅助栈为空，或者新来的元素比辅助栈的最后一个元素小，就添加这个元素
        if len(self.helper) == 0 or x <= self.helper[-1]:
            self.helper.append(x)
        else:
            # 否则， 辅助栈的最后一个元素再一次添加到辅助栈
            self.helper.append(self.helper[-1])

    def pop(self):
        # 出栈：注意要非空
        # 如果栈非空，辅助栈的栈顶元素就出栈，返回出栈元素
        if self.data:
            self.helper.pop()
            return self.data.pop()

    def top(self):
        # 获取栈顶元素
        if self.data:
            return self.data[-1]

    def getMin(self):
        # 获取最小值
        # 返回辅助栈的栈顶元素
        if self.helper:
            return self.helper[-1]

# 法二
class MinStack1:

    # 辅助栈和数据栈不同步
    # 关键 1：辅助栈的元素空的时候，必须放入新进来的数
    # 关键 2：新来的数小于或者等于辅助栈栈顶元素的时候，才放入（特别注意这里等于要考虑进去）
    # 关键 3：出栈的时候，辅助栈的栈顶元素等于数据栈的栈顶元素，才出栈，即"出栈保持同步"就可以了

    def __init__(self):
        # 数据栈
        self.data = []
        # 辅助栈
        self.helper = []

    def push(self, x):
        self.data.append(x)
        # 关键 1 和关键 2
        if len(self.helper) == 0 or x <= self.helper[-1]:
            self.helper.append(x)

    def pop(self):
        # 关键 3：【注意】不论怎么样，数据栈都要 pop 出元素
        top = self.data.pop()
        # 非空且相等才出栈
        if self.helper and top == self.helper[-1]:
            self.helper.pop()
        return top

    def top(self):
        if self.data:
            return self.data[-1]

    def getMin(self):
        if self.helper:
            return self.helper[-1]


```
