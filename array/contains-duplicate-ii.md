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
1. python中列表排序方法，sort方法与sorted方法。

    1. **sort排序方法是直接修改原列表list排序方法**，其调用形式为：**a.sort()**
。
        ```
        >>> a=[5,4,3,2,1]
        >>> a.sort()
        >>> 
        >>> a
        [1, 2, 3, 4, 5]
        ```
    2. **sorted()方法
保留原列表得到一个额外的已经排序好的列表**，其调用形式为**b = sorted(a)**。
         ```
        >>> a = [5,7,6,3,4,1,2]
        >>> b = sorted(a)
        >>> a
        [5, 7, 6, 3, 4, 1, 2]
        >>> b
        [1, 2, 3, 4, 5, 6, 7]
        ```     
        
        **sorted()方法可以用在任何数据类型的序列中，返回的总是一个列表形式**。
             
        ```
        >>> sorted('iplaypython.com')
        ['.', 'a', 'c', 'h', 'i', 'l', 'm', 'n', 'o', 'o', 'p', 'p', 't', 'y', 'y']
        ```     

        