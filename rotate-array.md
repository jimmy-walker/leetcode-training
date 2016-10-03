#Question
**Rotate an array of n elements to the right by k steps.**

#Example:
with n = 7 and k = 3, the array `[1,2,3,4,5,6,7]` is rotated to `[5,6,7,1,2,3,4]`.

#Hint
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

#Answer

## solution：

```python
class Solution:
    # @param nums, a list of integer
    # @param k, num of steps
    # @return nothing, please modify the nums list in-place.
    def rotate(self, nums, k):
        if not nums or not k:
            return None
        n = len(nums)
        k = k % n
        if k:
            nums[:k], nums[k:] = nums[-k:], nums[:-k]
```

#Knowledge：

1. 在python中 None,  False, 空字符串"", 0, 空列表[], 空字典{}, 空元组()都相当于False ，即：
```python
not None == not False == not '' == not 0 == not [] == not {} == not ()
```
   注意：[0]不是False。

   `if x is not None是最好的写法，清晰，不会出现错误，以后坚持使用这种写法。`

2. Python中的%是求余，特别是用于循环时涉及到的两个数之间可能原较小数k比n大的情况：k = k % n

3. 


