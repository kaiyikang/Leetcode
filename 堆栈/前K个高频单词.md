## 大顶堆需要熟悉参考第一版

~~~python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        dic = collections.Counter(words)
        heap, ans = [],[]
        for i in dic:
            # heappush(序号，内容)
            heapq.heappush(heap,(-dic[i],i))
        for _ in range(k):
            # heappop
            ans.append(heapq.heappop(heap)[1])
        return ans
~~~

