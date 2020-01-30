## 题目
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。
## 示例
示例1:

输入: ["flower","flow","flight"]
输出: "fl"
示例 2:

输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-common-prefix
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```python
import  numpy as np
class Solution:
    def longestCommonPrefix(self, strs) -> str:

        s = ''
        b = 0
        if strs != []:
            # x = np.argmin(len(strs))
            # print(x)
            all_len = [len(x) for x in strs]
            print(all_len)
            x = all_len.index(min(all_len))
            print(x)

            for j, val1 in enumerate(strs[x]):
                # print
                for i, val in enumerate(strs):
                    # 遍历所有str
                    # global val
                    if val1 == val[b]:
                        a = 1

                    else:
                        a = 0
                        break
                if a:
                    s += val1
                    if b < len(strs[x])-1:
                        b += 1
        return s
```
