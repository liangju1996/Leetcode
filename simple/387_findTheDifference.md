## 题目
给定两个字符串 s 和 t，它们只包含小写字母。

字符串 t 由字符串 s 随机重排，然后在随机位置添加一个字母。

请找出在 t 中被添加的字母。

 

示例:

输入：
s = "abcd"  
t = "abcde"

输出：
e

解释：  
'e' 是那个被添加的字母。

```python
# from collections import Counter
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        hmap1 = collections.Counter(s)
        hmap2 = collections.Counter(t)

        for i in t :
            if len(s) < len(t):
                if i in s and hmap1[i] == hmap2[i]:
                    continue
                else:
                    return i

class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        return chr(sum(map(ord, t)) - sum(map(ord, s)))
        ## ord: code chr: decode--------map(function,iterable,...)
```
