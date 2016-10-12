#Question
**Given an array of integers, find if the array contains any duplicates.**

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

#Answer
## solution1：this is my answer.
```python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        nums.sort()
        n = 0
        for i in xrange(1,len(nums)):
            if nums[n] == nums[i]:
                return True
            else:
                n = i
        return False
```

## solution2：
```python
class Solution:
    # @param {integer[]} nums
    # @return {boolean}
    def containsDuplicate(self, nums):
        return len(nums) > len(set(nums))
```

#Knowledge：
1. python中列表排序方法，sort方法与sorted方法。
    1. **sort排序方法是直接修改原列表list排序方法**，其调用形式为：**a.sort()**。
        ```
        >>> a=[5,4,3,2,1]
        >>> a.sort()
        >>> 
        >>> a
        [1, 2, 3, 4, 5]
        ```
    2. sorted()方法保留原列表得到一个额外的已经排序好的列表，其调用形式为**b = sorted(a)**。sorted()方法可以用在任何数据类型的序列中，返回的总是一个列表形式。
         ```
        >>> a = [5,7,6,3,4,1,2]
        >>> b = sorted(a)
        >>> a
        [5, 7, 6, 3, 4, 1, 2]
        >>> b
        [1, 2, 3, 4, 5, 6, 7]
        ```     



