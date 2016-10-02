#Question

**Given an array of integers, return indices of the two numbers such that they add up to a specific target.
**

You may assume that each input would have exactly one solution.


#Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].


#Hint

The return format had been changed to zero-based indices. Please read the above updated description carefully.

#Answer

## solution：

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        lookup = {}
        for i, num in enumerate(nums):
            if target - num in lookup: #当
                return [lookup[target - num], i]
            lookup[num] = i
        return []
```


#knowledge：
enumerate() 函数用于遍历序列中的元素的下标以及元素。

其常用形式for i, num in enumerate(nums):
