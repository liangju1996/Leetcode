## 题目： 两数之和 
给定一个整数数组 nums 和一个目标值 target
在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
## Note： 
不能重复利用数组中的元素
## 示例:  
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)):
            for j in range(len(nums)-1, i, -1):
                if nums[i] + nums[j] == target:
                    return i, j

# if __name__=="__main__":
#     # num = input()
#     nums = [2, 7, 11, 15]
#     target = 9
#     a = Solution()
#     # judge(nums, target)
#     print(a.twoSum(nums, target))
```
