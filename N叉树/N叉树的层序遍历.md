## 简易实现第一版

~~~python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root: return None
        ret = []
        stack = collections.deque([root])

        while stack:
            temp = []
            length = len(stack)
            for i in range(length):
                node = stack.popleft()
                temp.append(node.val)
                for kinder in node.children:
                    stack.append(kinder)
            ret.append(temp)
   
        return ret
~~~

