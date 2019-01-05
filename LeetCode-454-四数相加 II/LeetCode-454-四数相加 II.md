### 思路

给定四个包含整数的数组列表 A , B , C , D ,计算有多少个元组 (i, j, k, l) ，使得 A[i] + B[j] + C[k] + D[l] = 0。

为了使问题简单化，所有的 A, B, C, D 具有相同的长度 N，且 0 ≤ N ≤ 500 。所有整数的范围在 -228 到 228 - 1 之间，最终结果不会超过 231 - 1 。

### 示例
输入:
A = [ 1, 2]
B = [-2,-1]
C = [-1, 2]
D = [ 0, 2]

输出:
2

解释:
两个元组如下:
1. (0, 0, 0, 1) -> A[0] + B[0] + C[0] + D[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> A[1] + B[1] + C[0] + D[0] = 2 + (-1) + (-1) + 0 = 0

### Python 代码
* 思路：维护一个字典，键为AB各取一个元素的和，值为这个和出现的次数，在CD中各取一个元素求和，去相反数，如果相反数在字典中，则ans加上这个相反数对应的值

```python
class Solution:
    def fourSumCount(self, A, B, C, D):
        """
        :type A: List[int]
        :type B: List[int]
        :type C: List[int]
        :type D: List[int]
        :rtype: int
        """
        length = len(A)
        dic_AB = {}
        ans = 0
        for i in range(length):
            for j in range(length):
                sum_AB = A[i] + B[j]
                if sum_AB not in dic_AB:
                    dic_AB[sum_AB] = 0
                dic_AB[sum_AB] += 1
        for i in range(length):
            for j in range(length):
                sum_CD = C[i] + D[j]
                if -sum_CD in dic_AB:
                    ans += dic_AB[-sum_CD]
                    
        return ans
```