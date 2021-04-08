## 快速排序尝试找参考第一版

~~~python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        n = len(nums)
        # 目标是获得正序，倒数第k个
        target = n - k 
        left,right = 0,n-1
        while True:
        	# 整理，并且返回整理好的index
            index = self.foo(nums,left,right)
            if index == target:
                return nums[index]
            elif index < target:
            	# 这里注意不要出错，是找index的右边
                left = index + 1
                # Wrong! left += 1
            else: 
            	# index的左边，因为index大于target了。
                right = index - 1
                # Wrong! right -= 1
    def foo(self,nums,left,right):
        # 随机选择，为了加速
        random_index = random.randint(left, right)
        nums[random_index], nums[left] = nums[left], nums[random_index]
		# 始终以left位置为pivot
        pivot = nums[left]
        j = left
        # right+1 是因为默认right = n-1
        for i in range(left + 1, right +1):
            if nums[i] < pivot:
                j += 1
                nums[i] ,nums[j] = nums[j],nums[i]
        nums[left], nums[j] = nums[j], nums[left]
        return j
~~~

