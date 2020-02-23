##　题目
给定一个单词列表，只返回可以使用在键盘同一行的字母打印出来的单词。
#＃示例：
输入: ["Hello", "Alaska", "Dad", "Peace"]  
输出: ["Alaska", "Dad"]  
## 思路:求交集
```python
class Solution(object):
    def findWords(self, words):
        set1 = set('qwertyuiop')
        set2 = set('asdfghjkl')
        set3 = set('zxcvbnm')
        res = []
        for i in words:
            x = i.lower()
            setx = set(x)
            if setx<=set1 or setx<=set2 or setx<=set3:
                res.append(i)
        return res

作者：pandawakaka
链接：https://leetcode-cn.com/problems/keyboard-row/solution/jian-pan-xing-python3ji-he-qiu-jiao-ji-by-pandawak/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
