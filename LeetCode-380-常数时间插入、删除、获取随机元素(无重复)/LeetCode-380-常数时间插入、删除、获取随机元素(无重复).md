### 要求
设计一个支持在平均 时间复杂度 O(1) 下，执行以下操作的数据结构。

insert(val)：当元素 val 不存在时，向集合中插入该项。
remove(val)：元素 val 存在时，从集合中移除该项。
getRandom：随机返回现有集合中的一项。每个元素应该有相同的概率被返回。

### 示例
// 初始化一个空的集合。
RandomizedSet randomSet = new RandomizedSet();

// 向集合中插入 1 。返回 true 表示 1 被成功地插入。
randomSet.insert(1);

// 返回 false ，表示集合中不存在 2 。
randomSet.remove(2);

// 向集合中插入 2 。返回 true 。集合现在包含 [1,2] 。
randomSet.insert(2);

// getRandom 应随机返回 1 或 2 。
randomSet.getRandom();

// 从集合中移除 1 ，返回 true 。集合现在包含 [2] 。
randomSet.remove(1);

// 2 已在集合中，所以返回 false 。
randomSet.insert(2);

// 由于 2 是集合中唯一的数字，getRandom 总是返回 2 。
randomSet.getRandom();

### Python代码
* 思路：既然是要求在常数时间内的操作，很自然想到要用到数组的序号来操作，这里维护一个字典和一个列表，字典的键为元素，字典值为该元素在列表中的序号
* 在插入时，字典和列表均插入元素，字典中的值设为列表中元素的序号
* 在删除时，先在字典中获取待删除元素的序号，在列表中将末尾元素替换至该序号处，在字典中修改替换过来的元素的值，最后pop掉列表最后一个元素，同时删除掉字典中的val
* 在随机获取时，使用random随机获取一个序号，然后返回列表中对应序号的元素

```python
import random
class RandomizedSet:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        
        self.dic = {}
        self.lst = []

    def insert(self, val):
        """
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        :type val: int
        :rtype: bool
        """
        
        if val not in self.dic:
            self.lst.append(val)
            self.dic[val] = len(self.lst) - 1
            return True
        return False
        
        
    def remove(self, val):
        """
        Removes a value from the set. Returns true if the set contained the specified element.
        :type val: int
        :rtype: bool
        """
        
        if val in self.dic:
            idx = self.dic[val]
            self.lst[idx] = self.lst[-1]  # 与末尾元素交换
            self.dic[self.lst[idx]] = idx # 修改字典中交换元素的值
            self.lst.pop()
            del self.dic[val]
            return True
        return False
    
    def getRandom(self):
        """
        Get a random element from the set.
        :rtype: int
        """
        
        idx = random.randint(0, len(self.lst)-1)
        return self.lst[idx]
        


# Your RandomizedSet object will be instantiated and called as such:
# obj = RandomizedSet()
# param_1 = obj.insert(val)
# param_2 = obj.remove(val)
# param_3 = obj.getRandom()
```