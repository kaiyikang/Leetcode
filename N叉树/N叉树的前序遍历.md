## 递归成功第一版

~~~python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        ret = []
        def foo(root):
            if not root:return
            ret.append(root.val)
            for node in root.children:
                foo(node)
        foo(root)
        return ret
~~~



## 递归成功参考第二版

~~~python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:return None
        ret = []
        stack = [root]
        while stack:
            node = stack.pop()
            ret.append(node.val)
            # 这一步至关重要
            # 将重新整理stack，将左边的node放置在top，
            # 方便下一次pop出来
            stack = stack + node.children[::-1]
        return ret
~~~

