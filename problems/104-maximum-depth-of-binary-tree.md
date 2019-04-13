# 104. Maximum Depth of Binary Tree | 二叉树的最大深度

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, find its maximum depth.</p>

<p>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given binary tree <code>[3,9,20,null,null,15,7]</code>,</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>

<p>return its depth = 3.</p>
 instead-->
<p>给定一个二叉树，找出其最大深度。</p>

<p>二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例：</strong><br>
给定二叉树 <code>[3,9,20,null,null,15,7]</code>，</p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>

<p>返回它的最大深度&nbsp;3 。</p>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(!root){
            return 0;
        }
        return 1 + max(maxDepth(root->left), maxDepth(root->right));
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-depth-of-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-depth-of-binary-tree/)