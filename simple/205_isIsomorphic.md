## 题目
给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。
## 示例
示例 1:

输入: s = "egg", t = "add"  
输出: true


示例 2:

输入: s = "foo", t = "bar"  
输出: false

示例 3:

输入: s = "paper", t = "title"  
输出: true

## 说明:
你可以假设 s 和 t 具有相同的长度。

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        return [*map(s.index, s)] == [*map(t.index, t)]
        # 等价于 return [s.index(i) for i in s] == [t.index(i) for i in t]
        # str 类型数据拥有内置函数 index，输入一个子字符串，可以返回子字符串在 str 中第一次出现的索引，若不存在则报错
        # map(函数，可迭代对象) 将会对（参数2：可迭代对象）中的每个元素运用（参数1：函数）并将结果按顺序储存在一个迭代器中，返回这个迭代器
        # 使用 [*……] 可对对象解包，本题中 [*map……] 等效于 list(map……)
        # Python的list函数可以将其他数据类型转换为列表类型，并返回转换后的列表。当参数为空时，list函数可以创建一个空列表。

作者：QQqun902025048
链接：https://leetcode-cn.com/problems/isomorphic-strings/solution/1-xing-python-by-knifezhu-5/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
