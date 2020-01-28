# 题目：
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
# 示例：
示例 1:
输入: "abcabcbb"
输出: 3
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
    请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        sub = ''
        sum = [1]
        if s == '':
            return 0
        else:
            for i in range(0,len(s)):
                sub += s[i]
                print('as====', sub)
                for j in sub[0:len(sub)-1] :
                    print(i,j)
                    if s[i] == j:
                        sub = sub[i:]
                        break
                sum.append(len(sub))
                print('sub', sub)
                    # sum.append(len(sub)-1)
                    # sub = i

            print(sum)
            print(sub)

        return max(sum)

if __name__ == "__main__":
    s = 'dvdf'
    # s = input('please input:')
    a = Solution()
    print(a.lengthOfLongestSubstring(s))
    
```
