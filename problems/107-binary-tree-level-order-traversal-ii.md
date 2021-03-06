# 107. Binary Tree Level Order Traversal II | 二叉树的层次遍历 II

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <i>bottom-up level order</i> traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).</p>

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
return its bottom-up level order traversal as:<br />
<pre>
[
  [15,7],
  [9,20],
  [3]
]
</pre>
</p> instead-->
<p>给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）</p>

<p>例如：<br>
给定二叉树 <code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>

<p>返回其自底向上的层次遍历为：</p>

<pre>[
  [15,7],
  [9,20],
  [3]
]
</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

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
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>> res;
        if(!root){
            return res;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> vt;
        vt.insert(root);
        seq.push(root);
        while(!seq.empty()){
            int cnt = seq.size();
            vector<int> row;
            while(cnt--){
                TreeNode* tmp = seq.front();
                seq.pop();
                row.push_back(tmp->val);
                if(tmp->left && !vt.count(tmp->left)){
                    vt.insert(tmp->left);
                    seq.push(tmp->left);
                }
                if(tmp->right && !vt.count(tmp->right)){
                    vt.insert(tmp->right);
                    seq.push(tmp->right);
                }
            }
            res.push_back(row);
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-level-order-traversal-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-level-order-traversal-ii/)