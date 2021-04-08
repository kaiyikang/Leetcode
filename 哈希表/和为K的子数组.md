## 类似动态规划参考第一版

注释，这个比较难，需要想一会儿。

~~~python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        dic = {}
        dic[0] = 1
        ret = 0
        prenum = 0
        for num in nums:
            prenum += num
            # 上次累计 和 当前累计 之间差了K
     		# 说明算出了K
     		# 数量是上次累积的数量
            if prenum - k in dic:
                ret += dic[prenum-k]
            if prenum in dic:
                dic[prenum] += 1
            else:
                dic[prenum] = 1
        return ret
~~~

