### 要求
给定一棵二叉树，返回所有重复的子树。对于同一类的重复子树，你只需要返回其中任意一棵的根结点即可。

两棵树重复是指它们具有相同的结构以及相同的结点值。

### 示例
输入：
![屏幕快照 2018-12-30 下午4.40.47.png](resources/1AD76B73C1873ECA6C7F6BE3CB04A435.png =97x150)

重复的为：
![屏幕快照 2018-12-30 下午4.40.54.png](resources/3166936795C386865C95E775C4280C30.png =47x70)
![屏幕快照 2018-12-30 下午4.41.01.png](resources/1F97807D42F94FA8C12E8B76835BBDFB.png =30x34)

输出：需要以列表的形式返回上述重复子树的根结点。

### Python 代码
* 思路：对每一个子树采用先序遍历的方法，将遍历的结果保存为字符串作为键，值设为出现的次数，若值为1，则将子串的root添加到ans中，最后返回ans

```python
class Solution:
    def helper(self, root, dic, ans):
        if root is None:
            return '#'
        dic_key = str(root.val)+','+self.helper(root.left, dic, ans)+','+self.helper(root.right, dic, ans)
        if dic_key not in dic:
            dic[dic_key] = 0
        elif dic[dic_key] == 1:
            ans.append(root)
        dic[dic_key] += 1
        return dic_key
    
    def findDuplicateSubtrees(self, root):
        """
        :type root: TreeNode
        :rtype: List[TreeNode]
        """
        dic = {}
        ans = []
        self.helper(root, dic, ans)
        return ans
        
```