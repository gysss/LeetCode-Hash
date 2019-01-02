### 要求
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

### 示例
示例 1:
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

示例 2:
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

示例 3:
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。

### python代码
* 思路：维护一个列表，依次读取s中的字符，如果该字符不在列表中，则加入，并更新最大长度，若在列表中，则删除掉列表中前面到该字符的全部元素，并将该字符插入到最后

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        max_length = 0
        list_str = []
        for i in s:
            if i not in list_str:
                list_str.append(i)
                max_length = max_length if max_length > len(list_str) else len(list_str)
            else:
                del list_str[:list_str.index(i)+1]
                list_str.append(i)
        return max_length
```