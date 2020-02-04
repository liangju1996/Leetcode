## 题目
给定 S 和 T 两个字符串，当它们分别被输入到空白的文本编辑器后，判断二者是否相等，并返回结果。 # 代表退格字符。

 
## 示例
示例 1：

输入：S = "ab#c", T = "ad#c"  
输出：true  
解释：S 和 T 都会变成 “ac”。


示例 2：

输入：S = "ab##", T = "c#d#"  
输出：true  
解释：S 和 T 都会变成 “”。


示例 3：

输入：S = "a##c", T = "#a#c"  
输出：true  
解释：S 和 T 都会变成 “c”。


示例 4：

输入：S = "a#c", T = "b"  
输出：false  
解释：S 会变成 “c”，但 T 仍然是 “b”。

 

## 提示：


	1 <= S.length <= 200  
	1 <= T.length <= 200  
	S 和 T 只含有小写字母以及字符 '#'。
```python
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        stack1, stack2 = [], []
        for i in S:
            if i == '#':
                if  stack1:
                    stack1.pop()
            else:
                stack1.append(i)

        for i in T:
            if i == '#':
                if stack2:
                    stack2.pop()
            else:
                stack2.append(i) 

        if stack1 == stack2:
            return True
        else:
            return False
                         
```
