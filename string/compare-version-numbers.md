#Question
**Compare two version numbers version1 and version2.**

If version1 > version2 return 1, if version1 < version2 return -1, otherwise return 0.

You may assume that the version strings are non-empty and contain only digits and the `.` character.


The `.` character does not represent a decimal point and is used to separate number sequences.

For instance, `2.5` is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

#Example:
Here is an example of version numbers ordering:

```
0.1 < 1.1 < 1.2 < 13.37
```

#Answer
```python
class Solution(object):
    def compareVersion(self, version1, version2):
        """
        :type version1: str
        :type version2: str
        :rtype: int
        """
        list1 = version1.split(".")
        list2 = version2.split(".")

        if len(list1) > len(list2):
            for _ in xrange(len(list1) - len(list2)):
                list2.append("0")
        elif len(list1) < len(list2):
            for _ in xrange(len(list2) - len(list1)):
                list1.append("0")
        
        for i in xrange(len(list1)):
            if int(list1[i]) > int(list2[i]):
                return 1
            elif int(list1[i]) < int(list2[i]):
                return -1
            else:
                pass
        return 0
        # if int(list1[0]) > int(list2[0]):
        #     return 1
        # elif int(list1[0]) == int(list2[0]):
        #     if len(list1) == len(list2) == 1:
        #         return 0
        #     if len(list1) > len(list2):
        #         return 1
        #     if len(list1) < len(list2):
        #         return -1

        #     if int(list1[1]) > int(list2[1]):
        #         return 1
        #     elif int(list1[1]) == int(list2[1]):
        #         return 0
        #     else:
        #         return -1
        # else:
        #     return -1
```


##solution：



#Knowledge：
