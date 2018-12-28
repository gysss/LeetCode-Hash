### 要求
给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。

### 示例
输入: ["eat", "tea", "tan", "ate", "nat", "bat"],
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

### python代码
* 思路：建立一个键值对，其中键的设计很重要，键可以设计成每一个字符串排序后的结果，这样每读取一个字符串，先进行一次重排，如果重排后的新串在字典中，则将原本的字符串插入到该键对应的值中，如果不在字典中，则建立一个新的键值对

```python
class Solution:
    def rebuild(self, str):
        """
        重排字符串
        """
        ans = []
        for i in str:
            ans.append(i)
        ans.sort()
        return ''.join(ans)
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        dic = {}
        for str in strs:
            if str in dic:
                dic[str].append(str)
                continue
            str_ = self.rebuild(str)
            if str_ not in dic:
                dic[str_] = []
            dic[str_].append(str)
        return list(dic.values())
```