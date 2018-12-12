### 要求
不使用任何内建的哈希表库设计一个哈希集合

具体地说，你的设计应该包含以下的功能
add(value)：向哈希集合中插入一个值。
contains(value) ：返回哈希集合中是否存在这个值。
remove(value)：将给定值从哈希集合中删除。如果哈希集合中没有这个值，什么也不做。

### python代码
* 思路：利用字典，add时将key作为键，其对应的值设为1；remove时，将key对应的值设为0；检查是否存在时，如果字典中有key，返回其值是否等于1，若无则返回False

```python
class MyHashSet(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.data  = {}

    def add(self, key):
        """
        :type key: int
        :rtype: void
        """
        self.data[key] = 1

    def remove(self, key):
        """
        :type key: int
        :rtype: void
        """
        self.data[key] = 0 
        

    def contains(self, key):
        """
        Returns true if this set contains the specified element
        :type key: int
        :rtype: bool
        """
        if key in self.data:
            return self.data[key] == 1
        return False


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)
```

### C++代码

```c
class MyHashSet {
public:
    /** Initialize your data structure here. */
    vector<bool> data;
    MyHashSet() {
        data = vector<bool>(1000001,false);
    }
    
    void add(int key) {
        data[key]=true;
    }
    
    void remove(int key) {
        data[key]=false;
    }
    
    /** Returns true if this set contains the specified element */
    bool contains(int key) {
        return data[key];
    }
};

/**
 * Your MyHashSet object will be instantiated and called as such:
 * MyHashSet obj = new MyHashSet();
 * obj.add(key);
 * obj.remove(key);
 * bool param_3 = obj.contains(key);
 */
```