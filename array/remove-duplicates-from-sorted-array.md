# Question

**Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.**

Do not allocate extra space for another array, you must do this in place with constant memory.

# Example:

For example,
Given input array nums = `[1,1,2]`,

Your function should return length = `2`, with the first two elements of nums being `1` and `2` respectively. It doesn't matter what you leave beyond the new length.

# Answer

## solution1：

```python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        
        last, i = 0, 1
        while i < len(nums):
            if nums[last] != nums[i]:
                last += 1
                nums[last] = nums[i]
            i += 1
            
        return last + 1    
```

## solution2：this method which I wanna use is not accepted, cause it used extra space, which is not allowed.

```python
class Solution:
    def removeDuplicates(self, nums):
        nums = list(set(nums))
        return len(nums)
```

# Knowledge：

1. list与set间转换，用set(A)即可。注意定义时也是用set(list A)的形式来定义集合的。

2. 

