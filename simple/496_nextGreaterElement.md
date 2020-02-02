## 题目
给定两个没有重复元素的数组 nums1 和 nums2 ，其中nums1 是 nums2 的子集。找到 nums1 中每个元素在 nums2 中的下一个比其大的值。

nums1 中数字 x 的下一个更大元素是指 x 在 nums2 中对应位置的右边的第一个比 x 大的元素。如果不存在，对应位置输出-1。
## 示例
示例 1:

输入: nums1 = [4,1,2], nums2 = [1,3,4,2].
输出: [-1,3,-1]
解释:
    对于num1中的数字4，你无法在第二个数组中找到下一个更大的数字，因此输出 -1。
    对于num1中的数字1，第二个数组中数字1右边的下一个较大数字是 3。
    对于num1中的数字2，第二个数组中没有下一个更大的数字，因此输出 -1。
示例 2:

输入: nums1 = [2,4], nums2 = [1,2,3,4].
输出: [3,-1]
解释:
    对于num1中的数字2，第二个数组中的下一个较大数字是3。
    对于num1中的数字4，第二个数组中没有下一个更大的数字，因此输出 -1。
## 注意:

nums1和nums2中所有元素是唯一的。
nums1和nums2 的数组大小都不超过1000。

```python
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        stack, hashmap = list(), dict()
        for i in nums2:
            while len(stack) != 0 and stack[-1] < i:
                hashmap[stack.pop()] = i
            stack.append(i)
        return [hashmap.get(i,-1) for i in nums1]
        # dict.get(key, default=None)
        # Python 字典(Dictionary) get() 函数返回指定键的值，如果值不在字典中返回默认值。

class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        # 做一个dic，key为nums1中的元素，默认为-1
        # 单调栈，针对于栈顶元素，如果后面将要插入的数据比其大，则更新dic并出栈。
        dic = {}
        if not nums1:
            return []
        for x in nums1:
            dic[x] = -1
        stack = []
        for x in range(len(nums2)):
            while stack and nums2[stack[len(stack)-1]] < nums2[x]:
                dic[nums2[stack[len(stack)-1]]] = nums2[x]
                stack.remove(stack[len(stack)-1])
            stack.append(x)
        return [dic[x] for x in nums1]

```
