# 700. Search in a Binary Search Tree | 二叉搜索树中的搜索

## Question description

<!--If you want to use the English description, use <p>Given the root node of a binary search tree (BST) and a value. You need to find the node in the BST that the node&#39;s value equals the given value. Return the subtree rooted with that node. If such node doesn&#39;t exist, you should return NULL.</p>

<p>For example,&nbsp;</p>

<pre>
Given the tree:
        4
       / \
      2   7
     / \
    1   3

And the value to search: 2
</pre>

<p>You should return this subtree:</p>

<pre>
      2     
     / \   
    1   3
</pre>

<p>In the example above, if we want to search the value <code>5</code>, since there is no node with value <code>5</code>, we should return <code>NULL</code>.</p>

<p>Note that an empty tree is represented by <code>NULL</code>, therefore you would see the expected output (serialized tree format) as&nbsp;<code>[]</code>, not <code>null</code>.</p>
 instead-->
<p>给定二叉搜索树（BST）的根节点和一个值。 你需要在BST中找到节点值等于给定值的节点。 返回以该节点为根的子树。 如果节点不存在，则返回 NULL。</p>

<p>例如，</p>

<pre>
给定二叉搜索树:

        4
       / \
      2   7
     / \
    1   3

和值: 2
</pre>

<p>你应该返回如下子树:</p>

<pre>
      2     
     / \   
    1   3
</pre>

<p>在上述示例中，如果要找的值是 <code>5</code>，但因为没有节点值为 <code>5</code>，我们应该返回 <code>NULL</code>。</p>




## Solution

Language: **python3**  /  Runtime: 92 ms

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def searchBST(self, root, val):
        """
        :type root: TreeNode
        :type val: int
        :rtype: TreeNode
        """
        if root is None:
            return None
        elif root.val == val:
            return root
        elif root.val < val:
            return self.searchBST(root.right, val)
        else:
            return self.searchBST(root.left, val)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-in-a-binary-search-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-in-a-binary-search-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-in-a-binary-search-tree/)