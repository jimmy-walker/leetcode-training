# Question
**Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).**
# Example:
Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its bottom-up level order traversal as:
```
[
  [15,7],
  [9,20],
  [3]
]
```

# Answer
## solution：
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrderBottom(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []
        ans , level = [],[root]
        while level:
            ans.append([node.val for node in level]) #cause append just add a new element, if list , the list will be an element.
            temp = []
            for node in level:
                temp.extend([node.left,node.right])
            level = [leaf for leaf in temp if leaf]
        return ans[::-1]
```

# Knowledge：
1. 这道题目，我偷了个懒，将上一题的列表进行逆向索引。

2. 