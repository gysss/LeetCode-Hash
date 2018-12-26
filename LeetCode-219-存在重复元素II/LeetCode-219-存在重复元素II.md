### 要求
给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的绝对值最大为 k。

### 示例
输入: nums = [1,2,3,1], k = 3
输出: true

输入: nums = [1,0,1,1], k = 1
输出: true

输入: nums = [1,2,3,1,2,3], k = 2
输出: false

### Python代码
* 题目意思描述的不是很清楚，其实想表达的意思是在k个距离之内，nums中是否存在重复，可以用一个字典，键为nums中的数值，值为数值对应的下标，如果出现重复则计算下标差值是否在k之内，若在，则返回True，否则更新该数值所对应的字典中的值

```python
class Solution:
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        distance = {}
        for i in range(len(nums)):
            if nums[i] not in distance:
                distance[nums[i]] = i
            else:
                if i - distance[nums[i]] <= k:
                    return True
                else:
                    distance[nums[i]] = i
        return False
```