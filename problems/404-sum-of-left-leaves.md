# 404. Sum of Left Leaves | 左叶子之和

## Question description

<!--If you want to use the English description, use <p>Find the sum of all left leaves in a given binary tree.</p>

<p><b>Example:</b>
<pre>
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values <b>9</b> and <b>15</b> respectively. Return <b>24</b>.
</pre>
</p> instead-->
<p>计算给定二叉树的所有左叶子之和。</p>

<p><strong>示例：</strong></p>

<pre>
    3
   / \
  9  20
    /  \
   15   7

在这个二叉树中，有两个左叶子，分别是 9 和 15，所以返回 24</pre>

<p>&nbsp;</p>




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
    int sumOfLeftLeaves(TreeNode* root) {
        if(!root){
            return 0;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> vt;
        int res = 0;
        vt.insert(root);
        seq.push(root);
        while(!seq.empty()){
            TreeNode* tmp = seq.front();
            seq.pop();
            if(tmp->left && !vt.count(tmp->left)){
                vt.insert(tmp->left);
                seq.push(tmp->left);
                if(!tmp->left->left && !tmp->left->right){
                    res += tmp->left->val;
                }
            }
            if(tmp->right && !vt.count(tmp->right)){
                vt.insert(tmp->right);
                seq.push(tmp->right);
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-left-leaves/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-left-leaves/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-left-leaves/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-left-leaves/)