## 题目
给定一个包含大写字母和小写字母的字符串，找到通过这些字母构造成的最长的回文串。

在构造过程中，请注意区分大小写。比如 "Aa" 不能当做一个回文字符串。

## 注意:
假设字符串的长度不会超过 1010。
##　示例
示例 1: 

输入:　　
"abccccdd"

输出:　　
7

解释:　　
我们可以构造的最长的回文串是"dccaccd", 它的长度是 7。
```python
class Solution:
    def longestPalindrome(self, s: str) -> int:
        hmap = collections.Counter(s)
        l = []
        n = 0
        for k, v in hmap.items():
            if (v & 1) == 0:  
                n += v
            else:
                l.append(v)
        if l:
            n += max(l)
        return n
        ### 自己的解法, 没有考虑大于1的奇数也可以减去一个变成偶数加入回文序列

class Solution:
    def longestPalindrome(self, s):
        ans = 0
        for v in collections.Counter(s).itervalues():
            ans += v / 2 * 2
            if ans % 2 == 0 and v % 2 == 1:
                ans += 1
        return ans

```
