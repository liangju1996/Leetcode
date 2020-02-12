## 题目
给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的绝对值最大为 k。

示例 1:

输入: nums = [1,2,3,1], k = 3  
输出: true

示例 2:

输入: nums = [1,0,1,1], k = 1  
输出: true

示例 3:

输入: nums = [1,2,3,1,2,3], k = 2  
输出: false

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        r, d = k + 1, {}
        for i, n in enumerate(nums):
            r, d[n] = min(r, i - d.get(n, -k - 1)), i
        return r <= k
        
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        num2ind = {}
        for ind,v in enumerate(nums):
            if v in num2ind and ind-num2ind[v]<=k:
                return True
            else:
                num2ind[v]=ind
        return False

作者：312shan
链接：https://leetcode-cn.com/problems/contains-duplicate-ii/solution/python3-ha-xi-biao-by-312shan/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

```
