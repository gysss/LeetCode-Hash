### 要求
给定两个数组，编写一个函数来计算它们的交集。

### 示例
输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2]

### Python 代码

```python
class Solution(object):
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        nums1 = set(nums1)
        nums2 = set(nums2)
        
        ans = []
        
        for i in nums2:
            if i in nums1:
                ans.append(i)
        
        return ans
```