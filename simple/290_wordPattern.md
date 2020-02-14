## 题目
给定一种规律 pattern 和一个字符串 str ，判断 str 是否遵循相同的规律。

这里的 遵循 指完全匹配，例如， pattern 里的每个字母和字符串 str 中的每个非空单词之间存在着双向连接的对应规律。

示例1:

输入: pattern = "abba", str = "dog cat cat dog"  
输出: true

示例 2:

输入:pattern = "abba", str = "dog cat cat fish"  
输出: false

示例 3:

输入: pattern = "aaaa", str = "dog cat cat dog"  
输出: false

示例 4:

输入: pattern = "abba", str = "dog dog dog dog"  
输出: false

说明:  
你可以假设 pattern 只包含小写字母， str 包含了由单个空格分隔的小写字母。    

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/word-pattern
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```python
class Solution:
    def wordPattern(self, pattern: str, str: str) -> bool:
        hashmap={}
        tmp=str.split()
        if len(pattern)!=len(tmp):
            return False
        for i,j in zip(pattern,str.split()):
            if i not in hashmap and j not in hashmap.values():
                hashmap[i]=j    
            elif i not in hashmap and j in hashmap.values():
                return False
            elif i in hashmap:
                if hashmap[i]!=j:
                    return False
        return True

作者：jasss
链接：https://leetcode-cn.com/problems/word-pattern/solution/python-ha-xi-biao-by-jasss-3/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
优化
def wordPattern(self, pattern: str, str: str) -> bool:
    res=str.split()
    return list(map(pattern.index, pattern))==list(map(res.index,res))

作者：mou-xiao-wei
链接：https://leetcode-cn.com/problems/word-pattern/solution/pythonliang-xing-by-mou-xiao-wei/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
