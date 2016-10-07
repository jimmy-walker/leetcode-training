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
        if not nums: #以防止空list所造成的error
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

2. 这题只统计个数并且是有序列表，因此双指针，只记录相邻两者的比较，因为有序列表只可能相邻两者相等。不可能隔开一个数字还相等。**说明我思考时忽视了问题的特殊性，也侧面说明了我双指针的不熟练，需要多总结双指针的使用情景。**

3. **双指针问题——相邻移动**。当发现有两者相邻移动比较时，就要用双指针了。常见用法：    

   ```python    
   last, i = 0, 1        
   while i < len(nums): #i负责往前+1取值，所以需要比整体长度小
       if nums[last] != nums[i]:
           last += 1 #last就负责记录不相等的值得个数，只有发现了不相等的值了（只需和最近一个last比较，若不相等必然与前面所有的值都不等，因为是有序列表）
           nums[last] = nums[i] #因为如果之前有相等的情况下，那么i += 1就移动了，再次发现新的值，需要将此新值保存下来，覆盖掉之前相等的值得位置。
       i += 1 
   ```

