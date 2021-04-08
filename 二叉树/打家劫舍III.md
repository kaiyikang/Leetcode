~~~python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rob(self, root: TreeNode) -> int:
        def foo(node):
            # 返回的是数组 [打劫root的最大值，不打劫root的最大值]
            if not node: return [0,0]
            left = foo(node.left)
            right= foo(node.right)

            # return = [针对 root 进行打劫，不对 root 进行打劫]
            # 左： 自己的值+左右节点未打劫的最大值
            # 右： 因为没有自己的值，因此这里计算 打 or 不打 的最大值，然后左右相加（毕竟子节点打不打，都不影响）
            return [ left[1]+ right[1]+ node.val , max(left[0],left[1])+max(right[0],right[1])]
        # 注意是1 ！
        return max(foo(root))
~~~

