## 题目
使用队列实现栈的下列操作：

push(x) -- 元素 x 入栈  
pop() -- 移除栈顶元素  
top() -- 获取栈顶元素  
empty() -- 返回栈是否为空  
## Note:

你只能使用队列的基本操作-- 也就是 push to back, peek/pop from front, size, 和 is empty 这些操作是合法的。
你所使用的语言也许不支持队列。 你可以使用 list 或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。
你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。

```python
from queue import Queue

class MyStack:

    def __init__(self):
        """
        Initialize your data structure here.
        初始化两个队列
        """
        self.queue_push = Queue()
        self.queue_pop = Queue()

    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        直接添加x，x为队尾元素
        """
        self.queue_push.put(x)
        self.top_ele = x

    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """
        while (self.queue_push.qsize() > 1):
            self.top_ele = self.queue_push.get()
            # get（）：Remove and return an item from the queue.
            self.queue_pop.put(self.top_ele)
            # put（）：Put an item into the queue.
            # 删除q1中元素，将其添加到q2，直到，只剩一个元素
        res = self.queue_push.get()
        # 得到并删除最后一个元素（栈顶元素），返回
        # swap q1 q2
        self.queue_pop, self.queue_push = self.queue_push, self.queue_pop
        return res

    def top(self) -> int:
        """
        Get the top element.
        在上一步pop中实现的
        """
        return self.top_ele

    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        只需判断q1即可
        """
        return self.queue_push.empty() and self.queue_pop.empty()
        # empty（）：Return True if the queue is empty, False otherwise (not reliable!).

from queue import Queue

class MyStack1:

    def __init__(self):
        """
        Initialize your data structure here.
        初始化q1，q2
        """
        self.queue_push = Queue()
        self.queue_pop = Queue()

    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """
        self.queue_push.put(x)
        # 添加到q1
        self.shift()

    def shift(self):
        # 如果q2非空就把q2的元素出队并加到q1
        while (self.queue_pop.qsize()):
            self.queue_push.put(self.queue_pop.get())
        
        # 交换q1，2---q1变空，q2是全部的元素
        self.queue_pop, self.queue_push = self.queue_push, self.queue_pop

    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        删除q2的第一个元素
        """

        return self.queue_pop.get()

    def top(self) -> int:
        """
        Get the top element.
        """
        ##很奇怪，在python3中queue好像没有类似于top/peek的方法
        self.top_ele = self.queue_pop.get()
        # 删除q2的第一个元素
        # 添加q2的第一个元素
        self.push(self.top_ele)
        return self.top_ele
from queue import Queue

class MyStack2:

    def __init__(self):
        """
        Initialize your data structure here.
        这里只用一个元素
        """
        self.queue_push = Queue()

    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """
        self.queue_push.put(x)
        size = self.queue_push.qsize()
        # 当队列中的元素大于一个时，将队列中的元素调转顺序。
        # 方法为：将所有元素依次出队，然后分别入队
        while (size>1):
            self.queue_push.put(self.queue_push.get())
            size -= 1


    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """

        return self.queue_push.get()

    def top(self) -> int:
        """
        Get the top element.
        """
        ##很奇怪，在python3中queue好像没有类似于top/peek的方法
        top = self.queue_push.get()
        self.push(top)
        # 删除并添加
        return top

    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        """
        return self.queue_push.empty()

```
