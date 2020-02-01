## 题目：使用栈实现队列的下列操作：

push(x) -- 将一个元素放入队列的尾部。    
pop() -- 从队列首部移除元素。  
peek() -- 返回队列首部的元素。  
empty() -- 返回队列是否为空。  
## 示例:

MyQueue queue = new MyQueue();

queue.push(1);  
queue.push(2);  
queue.peek();  // 返回 1  
queue.pop();   // 返回 1  
queue.empty(); // 返回 false  
## 说明:

你只能使用标准的栈操作 -- 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。
你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。
假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）。

```python
## 官方解法1：
# 先将s1的元素倒入s2，
# 在s1中添加新元素
# 将s2中的元素倒入s1
class MyQueue:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.stack1 = []
        self.stack2 = []

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        # 两个栈倒，新来的元素总是在栈底（队尾进）
        if self.stack1 == None:
            self.stack1.append(x)
        else:
            while self.stack1:
                self.stack2.append(self.stack1.pop(-1))
            self.stack1.append(x)
            while self.stack2:
                self.stack1.append(self.stack2.pop(-1))

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        # 直接弹出，因为本来就是队头出
        return self.stack1.pop()

    def peek(self) -> int:
        """
        Get the front element.
        """
        if self.stack1:
            return self.stack1[-1]
        
    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        # 因为队列１存储了所有元素，所以只需要判断队列１
        return len(self.stack1) == 0

class MyQueue1:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.instack = []
        self.outstack = []

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        self.instack.append(x)
        

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        if len(self.outstack) == 0:
            while self.instack:
                self.outstack.append(self.instack.pop())

        return self.outstack.pop()
        

    def peek(self) -> int:
        """
        Get the front element.
        """
        if len(self.outstack) == 0:
            while self.instack:
                self.outstack.append(self.instack.pop())

        return self.outstack[-1]
        

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        return len(self.instack) == 0 and len(self.outstack) == 0
        


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()

class MyQueue2:

    def __init__(self):
        self.input, self.output = [], []

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        while self.output:
                self.input.append(self.output.pop())
        self.input.append(x)
        

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        while self.input:
            self.output.append(self.input.pop())
        return self.output.pop()
        

    def peek(self) -> int:
        """
        Get the front element.
        """
        while self.input:
            self.output.append(self.input.pop())
        return self.output[-1]

    
    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        # while self.input:
        #     self.output.append(self.input.pop())
        return not self.output and not self.input
        


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()


```
