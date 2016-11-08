# Question
**Find the sum of all left leaves in a given binary tree.**

# Example:
```
    3
   / \
  9  20
    /  \
   15   7
```

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.

# Answer
## solution：this is done by myself.
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def sumOfLeftLeaves(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        ans, level = 0, [root]
        while level:
            templeft, tempright = [], []
            for node in level:
                templeft.extend([node.left])
                tempright.extend([node.right])
            for node in templeft:
                if not node:
                    continue
                if not node.left and not node.right:
                    ans += node.val
            temp = templeft+tempright
            level = [leaf for leaf in temp if leaf]
        return ans       
```

# Knowledge：
1. 这道题目，一开始时候。

2. 
