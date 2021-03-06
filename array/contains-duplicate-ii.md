#Question
**Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.**

#Answer
## solution：
```python
class Solution:
    # @param {integer[]} nums
    # @param {integer} k
    # @return {boolean}
    def containsNearbyDuplicate(self, nums, k):
        lookup = {}
        for i, num in enumerate(nums):
            if num not in lookup:
                lookup[num] = i
            else:
                # It the value occurs before, check the difference.
                if i - lookup[num] <= k:
                    return True
                # Update the index of the value.
                lookup[num] = i
        return False
```

#Knowledge：
1. 这道第题目我还是使用常规的遍历循环去解决，很明显，在时间复杂度上，不能应付很长的列表。

2. 这一类属于two sum一样的**下标元素**类问题。关键是用enumerate去同时获得下标和元素，并且用辅助的字典记入进去（这就是类似**双指针——相邻移动的一种补充技术：更新变量减少指针**。），然后进行查找是否存在已有值。
        