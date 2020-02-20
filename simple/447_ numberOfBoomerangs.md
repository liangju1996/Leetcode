## 题目
给定平面上 n 对不同的点，“回旋镖” 是由点表示的元组 (i, j, k) ，其中 i 和 j 之间的距离和 i 和 k 之间的距离相等（需要考虑元组的顺序）。

找到所有回旋镖的数量。你可以假设 n 最大为 500，所有点的坐标在闭区间 [-10000, 10000] 中。

## 示例:

输入:  
[[0,0],[1,0],[2,0]]

输出:  
2

解释:  
两个回旋镖为 [[1,0],[0,0],[2,0]] 和 [[1,0],[2,0],[0,0]]

```Python
from collections import Counter
from scipy.special import perm

class Solution:
    def numberOfBoomerangs(self, points: List[List[int]]) -> int:
        count = 0
        for point in points:
            
            # distance2 记录对这个点来说的所有的距离
            distance2 = []
            for neighbor in points:
                distance2.append((point[0] - neighbor[0]) ** 2 + (point[1] - neighbor[1]) ** 2)
            
            frequency = Counter(distance2)
            
            for dist,num in frequency.items():
                if num >= 2:
                    count += perm(num,2)
                    
        return int(count)

# 作者：qsctech-sange
# 链接：https://leetcode-cn.com/problems/number-of-boomerangs/solution/yi-xing-python3-chao-jian-dan-jie-fa-by-qsctech-sa/
# 来源：力扣（LeetCode）
# 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
from collections import Counter
from scipy.special import perm
class Solution:
    def numberOfBoomerangs(self, points: List[List[int]]) -> int:
        return int(sum(sum(perm(num,2) for dist,num in Counter([(point[0] - neighbor[0]) ** 2 + (point[1] - neighbor[1]) ** 2 for neighbor in points]).items() if num >= 2) for point in points))

```
