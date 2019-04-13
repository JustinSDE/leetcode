# 145. Binary Tree Postorder Traversal | 二叉树的后序遍历

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <em>postorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;<code>[1,null,2,3]</code>
   1
    \
     2
    /
   3

<strong>Output:</strong>&nbsp;<code>[3,2,1]</code>
</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>
 instead-->
<p>给定一个二叉树，返回它的 <em>后序&nbsp;</em>遍历。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]  
   1
    \
     2
    /
   3 

<strong>输出:</strong> [3,2,1]</pre>

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
    vector<int> res;
    void postorder(TreeNode* node) {
        if (!node) return;
        postorder(node->left);
        postorder(node->right);
        res.push_back(node->val);
    }

    vector<int> postorderTraversal(TreeNode* root) {
        postorder(root);
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-postorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-postorder-traversal/)