## 递归

~~~python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        def foo(node):
            if not node:return

            foo(node.left)
            heapq.heappush(stack,node.val)
            foo(node.right)
        foo(root)
        return stack[k-1]

~~~

## 循环

~~~python
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while True:
            while root:
                stack.append(root)
                root = root.left
            
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
~~~

