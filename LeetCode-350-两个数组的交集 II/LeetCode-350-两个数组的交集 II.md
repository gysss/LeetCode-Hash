### 要求

给定两个数组，编写一个函数来计算它们的交集。

### 示例
输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2,2]

输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [4,9]

### Python代码

```python
class Solution:
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        dic = {}
        ans = []
        for i in nums1:
            if i not in dic:
                dic[i] = 0
            dic[i] += 1
        for i in nums2:
            if i in dic and dic[i] != 0:
                ans.append(i)
                dic[i] -= 1
        return ans
```