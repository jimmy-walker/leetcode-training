#Question
**Given an array and a value, remove all instances of that value in place and return the new length.**
Do not allocate extra space for another array, you must do this in place with constant memory.
The order of elements can be changed. It doesn't matter what you leave beyond the new length.

#Example:
Given input array nums = [3,2,2,3], val = 3
Your function should return length = 2, with the first two elements of nums being 2.

#Hint
Try two pointers.
Did you use the property of "the order of elements can be changed"?
What happens when the elements to remove are rare?

#Answer
## solution1：
```python
class Solution(object):
    def removeElement(self, nums, val):
    """
    :type nums: List[int]
    :type val: int
    :rtype: int
    """
    
    i, last = 0, len(nums) - 1
    while i <= last:
        if nums[i] == val:
            nums[i], nums[last] = nums[last], nums[i]
            last -= 1
        else:
            i += 1
    return last + 1
```

## solution2:（I prefer this one， cause it use the python advantage：list's function remove）
```python
class Solution(object):
    def removeElement(self, nums, val):
    """
    :type nums: List[int]
    :type val: int
    :rtype: int
    """
    while val in nums:
        nums.remove(val)
    return len(nums)
```

#Knowledge：
remove() 函数用于移除列表中某个值的第一个匹配项。

其语法为list.remove(obj)。