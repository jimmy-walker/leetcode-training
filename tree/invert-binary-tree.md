#Question
**Invert a binary tree. **

#Example:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

#Answer
##solution：
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root is not None:
            root.left, root.right = self.invertTree(root.right),self.invertTree(root.left)
        return root
```

#Knowledge：
1. 