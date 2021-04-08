## 动态规划背包问题第一版本

我们有一堆背包，载荷量j从target减少到0，当然其实可以不用到零，因为如果小于这石头的重量，也不用再装了。

那么 j 个包最多能装多少石头呢？面对一个新的i重石头，它有两个比较对象：

第一个，自己

第二个，装这个 i重 石头，包里还剩下 j - stones[i]的空间，那么这个空间最多能装多少石头呢？

这个问题的结果就被存储在了dp中，dp[j]代表的，j空间最多可以装多少石头，这个就和上面的问题对上了。我们想知道 j -stones[i] 空间，能装多少石头，那么就是 dp[ j - stone[i] ] 重的石头。

再加上石头重量stones[i]集可。

~~~python
class Solution:
    def lastStoneWeightII(self, stones: List[int]) -> int:
        total = sum(stones)
        dp = [0] * total
        # 目的 找到最大的一半
        target = total//2
        # 选择一块石头
        for i in range(len(stones)):
            # 选择一个能装j重量的背包，这个背包重量从目标减少到i重量（这个石头）
            for j in range(target,stones[i]-1,-1):
                # j包，能装多少石头？
                # 是上一次能装的石头量
                # 还是 这个包-这石头 能装的重量 + 这石头的重量
                dp[j] = max(dp[j],dp[j-stones[i]]+stones[i])
        return total - 2*dp[target]
~~~

