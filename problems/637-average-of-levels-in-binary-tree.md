# 637. Average of Levels in Binary Tree | 二叉树的层平均值

## Question description

<!--If you want to use the English description, use Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b>
    3
   / \
  9  20
    /  \
   15   7
<b>Output:</b> [3, 14.5, 11]
<b>Explanation:</b>
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The range of node's value is in the range of 32-bit signed integer.</li>
</ol>
</p> instead-->
<p>给定一个非空二叉树, 返回一个由每层节点平均值组成的数组.</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
    3
   / \
  9  20
    /  \
   15   7
<strong>输出:</strong> [3, 14.5, 11]
<strong>解释:</strong>
第0层的平均值是 3,  第1层是 14.5, 第2层是 11. 因此返回 [3, 14.5, 11].
</pre>

<p><strong>注意：</strong></p>

<ol>
	<li>节点值的范围在32位有符号整数范围内。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 16 ms

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
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double> res;
        if(!root){
            return res;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> visit;
        visit.insert(root);
        seq.push(root);
        while(!seq.empty()){
            int cnt = seq.size();
            int cntt = cnt;
            double sum = 0;
            while(cnt--){
                TreeNode* tmp = seq.front();
                seq.pop();
                if(tmp->left && !visit.count(tmp->left)){
                    visit.insert(tmp->left);
                    seq.push(tmp->left);
                }
                if(tmp->right && !visit.count(tmp->right)){
                    visit.insert(tmp->right);
                    seq.push(tmp->right);
                }
                sum += tmp->val;
            }
            res.push_back(sum / cntt);
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/average-of-levels-in-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/average-of-levels-in-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/average-of-levels-in-binary-tree/)