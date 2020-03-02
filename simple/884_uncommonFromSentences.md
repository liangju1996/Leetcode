# 题目：
从两个英文句子中找出一个不常用单词：在一个句子中出现一次，在另一个句子中未出现。
```python
class Solution:
    def uncommonFromSentences(self, A: str, B: str) -> List[str]:
        A = collections.Counter(A.split(' '))
        B = collections.Counter(B.split(' '))
        res = []
        print(A,B)
        for i, v1 in A.items():
            for j, v2 in B.items():
                if v1 == 1  and i not in B:
                    res.append(i)
                elif v2 == 1 and j not in A:
                    res.append(j)
        return set(res)

JavaPython
class Solution(object):
    def uncommonFromSentences(self, A, B):
        count = {}
        for word in A.split():
            count[word] = count.get(word, 0) + 1
        for word in B.split():
            count[word] = count.get(word, 0) + 1

        #Alternatively:
        #count = collections.Counter(A.split())
        #count += collections.Counter(B.split())

        return [word for word in count if count[word] == 1]
### 秒啊
class Solution:
    def uncommonFromSentences(self, A: str, B: str) -> List[str]:
        return [i for i in (A + ' ' + B).split() if (A + ' ' + B).split().count(i) == 1 ]

```
