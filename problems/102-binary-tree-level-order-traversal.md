# 102. Binary Tree Level Order Traversal | 二叉树的层次遍历

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <i>level order</i> traversal of its nodes' values. (ie, from left to right, level by level).</p>

<p>
For example:<br />
Given binary tree <code>[3,9,20,null,null,15,7]</code>,<br />
<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>
</p>
<p>
return its level order traversal as:<br />
<pre>
[
  [3],
  [9,20],
  [15,7]
]
</pre>
</p> instead-->
<p>给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。</p>

<p>例如:<br>
给定二叉树:&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回其层次遍历结果：</p>

<pre>[
  [3],
  [9,20],
  [15,7]
]
</pre>




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
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int> > res;
        if (!root) { return res; }
        queue<TreeNode*> Q;
        Q.push(root);
        while (!Q.empty()) {
            int n = Q.size();
            res.push_back(vector<int>());
            while (n--) {
                TreeNode* t = Q.front();
                Q.pop();
                res.back().push_back(t->val);
                if (t->left) {
                    Q.push(t->left);
                }
                if (t->right) {
                    Q.push(t->right);
                }
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-level-order-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-level-order-traversal/)