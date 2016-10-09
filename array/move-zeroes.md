#Question

**Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.**

The digits are stored such that the most significant digit is at the head of the list.

#Example
For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.

#Hint
You must do this in-place without making a copy of the array. Minimize the total number of operations.

#Answer

## solution：

```python

class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        z = 0
        for i in xrange(len(nums)):
            if nums[i]:
                nums[z],nums[i]=nums[i],nums[z]
                z += 1
```



#Knowledge：

1. 这道题收获很大，因为独立**思考**并**编程**，虽然最后没有成功，但是思路和答案一样，并且也发现了在思路转换到编程中出现的问题。**将解题分为思考和编码两个阶段。其中思考部分又分为空间和时间，涉及到思考流程图。在编码阶段分为将代码进行调节抽象。**

2. 思考部分，在空间上，如果不是in place的要求的话，直接把其中非0数值append到一个list中，0数值append到另一个list中，那么最后相加两个list即可。但由于是要求in place原位操作，所以需要用到双指针中的相邻移动。

3. 思考部分，在时间上。



