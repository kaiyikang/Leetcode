## 不存在cur.next的失败第一版

会出现cur.next = cur.next.next 报错，说不存在，解决方案是创建一个dummy让它存在。

~~~python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        pre = head 
        for _ in range(n):
            pre = pre.next
        cur = head 
        while pre and pre.next:
            pre = pre.next
            cur = cur.next
        
        cur.next = cur.next.next
        return head
~~~

## 造一个假头不怕next成功第二版

org: 1->None

new: 0 => 1 => None

n = 1

so, pre will go from 0 to None, because new n becomes 2 = 1 + 1.

cur = 0 , pre = None

=》 cur不动

cur = 0, pre = None

cur.next = cur.next.next = None

cur.next = None

head = None

~~~python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        pre = ListNode(0,head)
        cur = pre
        dummy = pre
        for _ in range(n+1):
            pre = pre.next

        while pre:
            cur = cur.next
            pre = pre.next
        
        cur.next = cur.next.next
        return dummy.next
~~~

