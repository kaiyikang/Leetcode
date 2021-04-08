~~~python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        left = 0
        right = len(nums)-1
        while left < right:
            mid = left + (right-left)//2
            # print(mid,nums[mid])
            if nums[mid] > nums[right]:
                left = mid +1
            elif nums[mid] < nums[right]:
                right = mid
            else: right -=1 # 由于只和右边比较，因此减少右边
        return nums[right]
~~~

