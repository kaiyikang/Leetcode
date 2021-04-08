## 使用heap排序，快块搞定

~~~python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        dummy = ListNode(0)
        cur = dummy
        heap = []
        for node in lists:
            while node:
                heapq.heappush(heap,node.val)
                node = node.next
        while heap:
            temp = ListNode(heapq.heappop(heap))
            cur.next = temp
            cur = cur.next
        return dummy.next
~~~

