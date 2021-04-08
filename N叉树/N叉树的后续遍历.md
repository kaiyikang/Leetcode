## 递归成功第一版

~~~python
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        ret = []
        def foo(root):
            if not root:
                return 
            for node in root.children:
                foo(node)
            ret.append(root.val)
        foo(root)
        return ret
~~~



## 递归成功参考第二版

~~~python
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        if not root:return []
        ret = []
        stack = [root]
        while stack:
            node = stack.pop()
            ret.append(node.val)
            stack = stack + node.children
        return ret[::-1]
~~~

