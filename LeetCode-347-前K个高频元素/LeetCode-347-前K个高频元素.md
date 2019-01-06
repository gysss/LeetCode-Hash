### 要求
给定一个非空的整数数组，返回其中出现频率前 k 高的元素

### 示例
示例 1:
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]

示例 2:
输入: nums = [1], k = 1
输出: [1]

你可以假设给定的 k 总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
### Python代码

```python
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        dic = {}      
        for i in nums:
            if i not in dic:
                dic[i] = 0
            dic[i] += 1
        a = sorted(dic.items(), key=lambda item:item[1],reverse=True) 
        # 按值排序，reverse默认为False，为升序，True为降序，返回的是一个列表，列表元素为有序的键值元组
        ans = []
        for i in range(k):
            ans.append(a[i][0])
        return ans
```