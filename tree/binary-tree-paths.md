#Question
**Given a binary tree, return all root-to-leaf paths.** 

#Example:
For example, given the following binary tree: 
```
   1
 /   \
2     3
 \
  5
```
All root-to-leaf paths are: 
```
["1->2->5", "1->3"]
```

#Answer
##solution：
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    # @param {TreeNode} root
    # @return {string[]}

    def binaryTreePaths(self, root):
        if not root:
            return []
        if not root.left and not root.right:
            return [str(root.val)]
        treepaths = [str(root.val)+'->'+path for path in self.binaryTreePaths(root.left)]
        treepaths += [str(root.val)+'->'+path for path in self.binaryTreePaths(root.right)]
        return treepaths
```

#Knowledge：
1. 这道题目与之前的层遍历不同，是需要按照路径遍历。**树遍历问题——按路径遍历**，记住该公式。