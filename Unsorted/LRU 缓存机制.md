## ordereddict成功第一版

~~~python
class LRUCache:

    def __init__(self, capacity: int):
        self.dic = collections.OrderedDict()
        self.cap = capacity

    def get(self, key: int) -> int:
    # 如果读取了，把它放在尾端，说明用过
        if key in self.dic:
            val = self.dic[key]
            self.dic.pop(key)
            self.dic[key] = val
            return val
        return -1


    def put(self, key: int, value: int) -> None:
        # 如果存在，放到末尾替换
        if key in self.dic:
            self.dic.pop(key)
            self.dic[key] = value
            return
		# 如果不存在，看cap计数器
		# 大于零，说明还可以继续往里面存
		# 小于零，把第一个pop出来，末尾填入新的。
        if self.cap > 0:
            self.dic[key] = value
            self.cap -= 1
        else:
            for i in self.dic.keys():
                self.dic.pop(i)
                break
            self.dic[key] = value
            
# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
~~~

