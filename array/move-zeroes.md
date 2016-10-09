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

1. 这道题收获很大，因为独立**思考**并**编程**，虽然最后没有成功，但是思路和答案一样，并且也发现了在思路转换到编程中出现的问题。**将解题分为思考和编程两个阶段。其中思考部分又分为空间和时间，涉及到思考流程图。在编码阶段分为将代码进行调节与抽象(将循环的各个次数平行写出从而帮助抽象)。**

2. 思考部分，在空间上，如果不是in place的要求的话，直接把其中非0数值append到一个list中，0数值append到另一个list中，那么最后相加两个list即可。但由于是要求in place原位操作，所以需要用到双指针中的相邻移动。

3. 思考部分，结合思考流程图来考虑时间上操作。写出了树结构来分析情况，从而制订了大致的时间安排：两个指针，一个z找0元素，不需要增长到list最后；另一个i找非0元素，需要增长到list最后，找到后与前面的z进行元素对换。`nums[z],nums[i]=nums[i],nums[z]`

4. 编程部分，根据之前的思考部分，将代码实现。
    
    1. 因为i要从0开始到list长度，所以用for循环。`for i in xrange(len(nums)):`注意在思考部分对换操作是用`nums[i],nums[i+1]=nums[i+1],nums[i]`，这里需要留心到for会自动增长i，因此不用i+1了，发挥双指针优势，从而帮助编程中的抽象。（**我在编程时一直使用i+1与i对换，从而导致程序无法抽象出来的错误。切记。**）

    2. 当第一个元素判断其为非0时：
        ```python
            if nums[i]:                
                z += 1
        ```
       而当第一个元素判断其为0时，再循环到第二次时（i自动加1）：
        ```python
            if nums[i]:
                nums[z],nums[i]=nums[i],nums[z]                              
                z += 1
        ```
       这里为了抽象方便，将循环的各个次数平行写出从而帮助抽象。此外为了代码的简洁性，在第一次的时候，也加入对换操作，虽然是与自身对换而已。
    



