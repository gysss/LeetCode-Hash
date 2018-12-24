### 要求

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

### 示例
s = "leetcode"
返回 0.

s = "loveleetcode",
返回 2.

### python代码
* 维护一个hash表，键为字符，值为出现个数，返回第一个值为1的键的下标

```python
class Solution:
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        str_hash = {}
        for i in range(len(s)):
            if s[i] not in str_hash:
                str_hash[s[i]] = 0
            str_hash[s[i]] += 1
        for i in str_hash.keys():
            if str_hash[i] == 1:
                return s.index(i)
        return -1
```