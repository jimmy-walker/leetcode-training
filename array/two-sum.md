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
            if target - num in lookup: #思想为对每一个元素a去查是否有另一个使其满足条件的数b存在，那么就需要将每一个元素存到另一个数据结构中去以作为判断（因为如果不存新的数据结构的话，直接遍历会使得序号访问变复杂，比如说空出当前值a，所以索性就新建一个数据结构保存已经检查完的数），从而达到依次判断的效果。
            #注意判断字典中值的方法，直接if a in dict:即可
                return [lookup[target - num], i]
            lookup[num] = i
        return []
```


#Knowledge：
1. enumerate() 函数用于遍历序列中的元素的下标以及元素。

   其常用形式for i, num in enumerate(nums):

2. 注意判断字典中值的方法，直接if a in dict:即可
