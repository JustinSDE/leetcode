# 94. Binary Tree Inorder Traversal | 二叉树的中序遍历

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <em>inorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>Output:</strong> [1,3,2]</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>
 instead-->
<p>给定一个二叉树，返回它的<em>中序&nbsp;</em>遍历。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>输出:</strong> [1,3,2]</pre>

<p><strong>进阶:</strong>&nbsp;递归算法很简单，你可以通过迭代算法完成吗？</p>




## Solution

Language: **cpp**  /  Runtime: 0 ms

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
    void dfs(TreeNode* node, vector<int>& res) {
        if (!node) {
            return;
        }
        if (node->left) {
            dfs(node->left, res);
        }
        res.push_back(node->val);
        if (node->right) {
            dfs(node->right, res);
        }
    }
    
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        dfs(root, res);
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-inorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-inorder-traversal/)