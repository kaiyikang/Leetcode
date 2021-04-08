## 前缀和+递归=再来一遍

~~~python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        # map[prefix value] = num of node
        self.hashmap = collections.defaultdict(int)
        self.hashmap[0] = 1
        target = sum
        
        def foo(node,cur_sum):
            if not node:return 0
            # 以该 node 作为 root，向下寻找
            ret = 0
            # 更新当前路径和
            cur_sum += node.val
            # 查询该节点的祖先节点中符合条件的个数
            ret += self.hashmap[cur_sum-target]
            # 更新 prefix_value = cur_sum 下的数量
            self.hashmap[cur_sum] = self.hashmap[cur_sum] + 1
            # 递归
            left = foo(node.left,cur_sum)
            right =foo(node.right,cur_sum)

            ret += left + right
            # 取消该点的统计，恢复一下
            self.hashmap[cur_sum] = self.hashmap[cur_sum] - 1
            return ret
        
        return foo(root,0)
~~~

