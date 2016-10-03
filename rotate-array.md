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
            nums[:k], nums[k:] = nums[-k:], nums[:-k] #交换两段数据，注意这种用法，不要顾忌不使用第三方会影响数据保存
```

#Knowledge：

1. 在python中 None,  False, 空字符串"", 0, 空列表[], 空字典{}, 空元组()都相当于False ，即：
```python
not None == not False == not '' == not 0 == not [] == not {} == not ()
```
   注意：[0]不是False。

   `if x is not None是最好的写法，清晰，不会出现错误，以后坚持使用这种写法。`

2. Python中的%是求余，特别是用于循环时涉及到的两个数之间可能原较小数k比n大的情况：k = k % n

3. nums[:k], nums[k:] = nums[-k:], nums[:-k] 交换两段数据，注意这种用法，不要顾忌不使用第三方会影响数据保存

4. python索引，正数索引[0:n-1]；使用负数索引时，Python会从右边，也就是从最后 1 个元素开始计数。最后 1 个元素的位置编号是-1。[-n:-1]。
    
    `第1个索引的元素是包含在分片内的，而第2个则不包含在分片内。`
   
    `如果分片中最左边的索引比它右边的晚出现在序列中，结果就是一个空的序列。numbers[-3:0]，结果为[]`

