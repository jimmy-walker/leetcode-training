#Question
**Given an array of size n, find the majority element. The majority element is the element that appears more than `⌊ n/2 ⌋` times.**

You may assume that the array is non-empty and the majority element always exist in the array.

#Answer
## solution：
```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        record = {}
        for i in xrange(len(nums)):
            if nums[i] not in record:
                record[nums[i]] = 1
            else:
                record[nums[i]] += 1
        for i in record:
            if record[i] > len(nums)/2:
                return i
```

#Knowledge：

1. 可能这个算法并不是最佳的复杂度，但是终究能解决问题。此外，还在本地进行调试，从而帮助了这个程序。

2. 字典的遍历方法：

    ```python

    l = [(x,x) for x in xrange(10000)]
    d = dict(l)
 
    from time import clock
 
    t0=clock()
    for i in d:
     t = i + d[i]
    t1=clock()
 
    for k,v in d.items():
     t = k + v
    t2=clock()
 
    for k,v in d.iteritems():
     t = k + v
    t3=clock()
 
    print t1-t0, t2-t1, t3-t2

    ```
    结果为`0.00184039735833 0.00326492977712 0.00214993552657`，可见第一种方法速度最快。
    
