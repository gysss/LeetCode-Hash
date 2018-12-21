### 要求
给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。

### 示例
输入: s = "egg", t = "add"
输出: true

输入: s = "foo", t = "bar"
输出: false

### Python代码

```python
class Solution(object):
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        return self.iso(s,t) and self.iso(t,s)
        
    def iso(self,s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        mapx = {}
        for i in range(len(s)):
            if s[i] not in mapx:
                mapx[s[i]] = t[i]
            elif s[i] in mapx:
                if t[i] != mapx[s[i]]:
                    return False
        return True
```