### 要求
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

### 示例
输入: [4,1,2,1,2]
输出: 4

### Python代码
* 我的：采用了字典统计每个数出现的次数，最后返回次数为1的

```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = {}
        for i in nums:
            if i not in count:
                count[i] = 1
            else:
                count[i] += 1
        for j in count.keys():
            if count[j] == 1:
                return j
```

* 大佬的：利用了异或的性质，出现了两次的异或后为0，出现了一次的与0异或得本身，最后返回即可

```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        a=nums[0]
        for i in range(1,len(nums)):
            a=a^nums[i]
        return a
```