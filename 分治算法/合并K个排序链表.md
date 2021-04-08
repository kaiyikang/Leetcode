## 分治参考第一版

~~~python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	# 只处理两个
    def mergeTwo(self,l1,l2):
        dummy = ListNode(0)
        ret =dummy
        while l1 or l2:
            if l1 and l2 and l1.val <= l2.val:
                dummy.next = l1
                l1 = l1.next
            elif l1 and l2 and l1.val > l2.val:
                dummy.next = l2
                l2 = l2.next
            elif l1 and not l2:
                dummy.next = l1
                l1 = l1.next
            elif not l1 and l2:
                dummy.next = l2
                l2 = l2.next
            dummy = dummy.next 
        return ret.next
    
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        if not lists:return None
        # 合并N个
        def merge(tmp, l,r):
            if l == r: return tmp[l]
            if l > r: None
            mid = (l+r)>>1
            return self.mergeTwo(merge(tmp,l,mid),merge(tmp,mid+1,r))
        return merge(lists,0,len(lists)-1)
~~~

