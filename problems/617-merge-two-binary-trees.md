# 617. Merge Two Binary Trees | 合并二叉树

## Question description

<!--If you want to use the English description, use <p>Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.</p>

<p>You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
<b>Output:</b> 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
</pre>

<p>&nbsp;</p>

<p><b>Note:</b> The merging process must start from the root nodes of both trees.</p>
 instead-->
<p>给定两个二叉树，想象当你将它们中的一个覆盖到另一个上时，两个二叉树的一些节点便会重叠。</p>

<p>你需要将他们合并为一个新的二叉树。合并的规则是如果两个节点重叠，那么将他们的值相加作为节点合并后的新值，否则<strong>不为&nbsp;</strong>NULL 的节点将直接作为新二叉树的节点。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
<strong>输出:</strong> 
合并后的树:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
</pre>

<p><strong>注意:</strong>&nbsp;合并必须从两个树的根节点开始。</p>




## Solution

Language: **python3**  /  Runtime: 152 ms

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def mergeTrees(self, t1, t2):
        """
        :type t1: TreeNode
        :type t2: TreeNode
        :rtype: TreeNode
        """
        if t1 is None and t2 is None:
            return None
        else:
            if t1 is None:
                res = TreeNode(t2.val)
                res.left = self.mergeTrees(None, t2.left)
                res.right = self.mergeTrees(None, t2.right)
            elif t2 is None:
                res = TreeNode(t1.val)
                res.left = self.mergeTrees(t1.left, None)
                res.right = self.mergeTrees(t1.right, None)
            else:
                res = TreeNode(t1.val + t2.val)
                res.left = self.mergeTrees(t1.left, t2.left)
                res.right = self.mergeTrees(t1.right, t2.right)
            return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-two-binary-trees/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-two-binary-trees/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-two-binary-trees/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-two-binary-trees/)