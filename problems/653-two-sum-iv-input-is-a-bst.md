# 653. Two Sum IV - Input is a BST | 两数之和 IV - 输入 BST

## Question description

<!--If you want to use the English description, use <p>Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

<b>Output:</b> True
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

<b>Output:</b> False
</pre>

<p>&nbsp;</p>
 instead-->
<p>给定一个二叉搜索树和一个目标结果，如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 true。</p>

<p><strong>案例 1:</strong></p>

<pre>
<strong>输入:</strong> 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

<strong>输出:</strong> True
</pre>

<p>&nbsp;</p>

<p><strong>案例 2:</strong></p>

<pre>
<strong>输入:</strong> 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

<strong>输出:</strong> False
</pre>

<p>&nbsp;</p>




## Solution

Language: **cpp**  /  Runtime: 36 ms

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
    bool findTarget(TreeNode* root, int k) {
        if(!root){
            return false;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> vt;
        multiset<int> vals;
        vt.insert(root);
        seq.push(root);
        while(!seq.empty()){
            TreeNode* tmp = seq.front();
            seq.pop();
            if(tmp->left && !vt.count(tmp->left)){
                vt.insert(tmp->left);
                seq.push(tmp->left);
            }
            if(tmp->right && !vt.count(tmp->right)){
                vt.insert(tmp->right);
                seq.push(tmp->right);
            }
        }
        for(TreeNode* node : vt){
            vals.insert(node->val);
        }
        for(int val : vals){
            int target = k - val;
            if(vals.count(target) > (int)(target == val)){
                return true;
            }
        }
        return false;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/description/)

Solution: [LeetCode](https://leetcode.com/articles/two-sum-iv-input-is-a-bst/)  /  [LeetCode中国](https://leetcode-cn.com/articles/two-sum-iv-input-is-a-bst/)