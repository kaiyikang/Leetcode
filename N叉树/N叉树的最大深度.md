## 深度优先成功第一版

~~~python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def maxDepth(self, root: 'Node') -> int:
        if not root:
            return 0
        elif root.children == []:
            return 1
        else:
            height = [self.maxDepth(c) for c in root.children]
            return max(height) +1 
~~~



## 广度优先第二版

~~~python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def maxDepth(self, root: 'Node') -> int:
        ans = 0
        stack = []
        # 如果root存在，把高度和节点存入stack
        if root:
            stack.append((1,root))
        while stack != []:
            n = len(stack)
            for i in range(n):
                # 获得这个节点和对应高度
                depth,root = stack.pop()
                # 更新最深
                ans = max(ans,depth)
                # 将children加入stack
                for node in root.children:
                    stack.append((depth+1,node))
        return ans
~~~

