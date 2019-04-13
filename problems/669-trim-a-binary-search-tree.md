# 669. Trim a Binary Search Tree | 修剪二叉搜索树

## Question description

<!--If you want to use the English description, use <p>
Given a binary search tree and the lowest and highest boundaries as <code>L</code> and <code>R</code>, trim the tree so that all its elements lies in <code>[L, R]</code> (R >= L). You might need to change the root of the tree, so the result should return the new root of the trimmed binary search tree.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> 
    1
   / \
  0   2

  L = 1
  R = 2

<b>Output:</b> 
    1
      \
       2
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

<b>Output:</b> 
      3
     / 
   2   
  /
 1
</pre>
</p> instead-->
<p>给定一个二叉搜索树，同时给定最小边界<code>L</code>&nbsp;和最大边界&nbsp;<code>R</code>。通过修剪二叉搜索树，使得所有节点的值在<code>[L, R]</code>中 (R&gt;=L) 。你可能需要改变树的根节点，所以结果应当返回修剪好的二叉搜索树的新的根节点。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 
    1
   / \
  0   2

  L = 1
  R = 2

<strong>输出:</strong> 
    1
      \
       2
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

<strong>输出:</strong> 
      3
     / 
   2   
  /
 1
</pre>




## Solution

Language: **cpp**  /  Runtime: 20 ms

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
    TreeNode* trimBST(TreeNode* root, int L, int R) {
        if (!root) { return root; }
        if (root->val < L) {
            return trimBST(root->right, L, R);
        }
        if (root->val > R) {
            return trimBST(root->left, L, R);
        }
        
        root->left = trimBST(root->left, L, R);
        root->right = trimBST(root->right, L, R);
        return root;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/trim-a-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/trim-a-binary-search-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/trim-a-binary-search-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/trim-a-binary-search-tree/)