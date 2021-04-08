## 深度优先 递归

~~~python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pathSum(self, root: TreeNode, targetSum: int) -> List[List[int]]:
        self.ret = []
        def foo(node,target,temp):
            if not node:return
            # 放入该节点 
            temp.append(node.val)
            # 如果是叶子
            if not node.left and not node.right and node.val == target:
                # 深拷贝
                self.ret.append(temp[:])
            # 下潜
            foo(node.left, target-node.val,temp)
            foo(node.right,target-node.val,temp)
            # 弹出该节点
            temp.pop()
        foo(root,targetSum,[])
        return self.ret
~~~

