## 直接用heap计算成功第一版

~~~python
class Solution:
    def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
        import math
        heap = []
        for i in points:
            heapq.heappush(heap,(math.sqrt(i[0]**2+i[1]**2),i))
        ans = []
        for _ in range(K):
            ans.append(heapq.heappop(heap)[1])
        return ans
~~~



