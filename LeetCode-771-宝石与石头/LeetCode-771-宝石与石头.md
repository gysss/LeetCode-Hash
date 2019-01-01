### 要求
给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。
J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

### 示例
输入: J = "aA", S = "aAAbbbb"
输出: 3

输入: J = "z", S = "ZZ"
输出: 0

### Python代码

```python
class Solution:
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        dic = {}
        for i in J:
            dic[i] = 0
        for j in S:
            if j in dic:
                dic[j] += 1
        return sum(dic.values())
```