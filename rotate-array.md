#Question
**Rotate an array of n elements to the right by k steps.**

#Example:
with n = 7 and k = 3, the array `[1,2,3,4,5,6,7]` is rotated to `[5,6,7,1,2,3,4]`.

#Hint
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

#Answer

## solution1：

```python
class Solution:
    # @param nums, a list of integer
    # @param k, num of steps
    # @return nothing, please modify the nums list in-place.
    def rotate(self, nums, k):
        if not nums or not k:
            return None

        k %= len(nums)

        if k:
            nums[:k], nums[k:] = nums[-k:], nums[:-k]
```

## solution2：

```python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k = k % n
        nums[:] = nums[n-k:] + nums[:n-k]
```

#Knowledge：

1. enumerate() 函数用于遍历序列中的元素的下标以及元素。

 其常用形式for i, num in enumerate(nums):



2. 注意判断字典中值的方法，直接if a in dict:即可


