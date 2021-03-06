# 5017. Sum of Root To Leaf Binary Numbers | 从根到叶的二进制数之和

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, each node has value <code>0</code>&nbsp;or <code>1</code>.&nbsp; Each root-to-leaf path represents a binary number starting with the most significant bit.&nbsp; For example, if the path is <code>0 -&gt; 1 -&gt; 1 -&gt; 0 -&gt; 1</code>, then this could represent <code>01101</code> in binary, which is <code>13</code>.</p>

<p>For all leaves in the tree, consider the numbers represented by the path&nbsp;from the root to that leaf.</p>

<p>Return the sum of these numbers <strong>modulo <code>10^9 + 7</code></strong>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<p><span id="example-output-1"><img alt="" src="https://assets.leetcode.com/uploads/2019/04/04/sum-of-root-to-leaf-binary-numbers.png" style="width: 304px; height: 200px;" /></span></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,0,1,0,1,0,1]</span>
<strong>Output: </strong><span id="example-output-1">22</span>
<strong>Explanation: </strong>(100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>The number of nodes in the tree is between <code>1</code> and <code>1000</code>.</li>
	<li>node.val is <code>0</code> or <code>1</code>.</li>
</ol> instead-->
<p>给出一棵二叉树，其上每个结点的值都是&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code>&nbsp;。每一条从根到叶的路径都代表一个从最高有效位开始的二进制数。例如，如果路径为&nbsp;<code>0 -&gt; 1 -&gt; 1 -&gt; 0 -&gt; 1</code>，那么它表示二进制数&nbsp;<code>01101</code>，也就是&nbsp;<code>13</code>&nbsp;。</p>

<p>对树上的每一片叶子，我们都要找出从根到该叶子的路径所表示的数字。</p>

<p>以<strong>&nbsp;<code>10^9 + 7</code></strong>&nbsp;为<strong>模</strong>，返回这些数字之和。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/04/05/sum-of-root-to-leaf-binary-numbers.png" style="height: 200px; width: 304px;"></p>

<pre><strong>输入：</strong>[1,0,1,0,1,0,1]
<strong>输出：</strong>22
<strong>解释：</strong>(100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>树中的结点数介于 <code>1</code> 和 <code>1000</code> 之间。</li>
	<li>node.val 为&nbsp;<code>0</code> 或&nbsp;<code>1</code>&nbsp;。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 12 ms

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
    vector<int> path;
    int res = 0;
    
    void dfs(TreeNode* node) {
        if (!node) return;
        path.push_back(node->val);
        if (node->left)
            dfs(node->left);
        if (node->right)
            dfs(node->right);
        // 到了叶子节点
        if (!node->left && !node->right) {
            int num = 0;
            for (int i = 0; i < (int)path.size(); i++) {
                if (path[i] == 1) {
                    num |= (1 << (int)path.size() - i - 1);
                }
            }
            // for (int p : path) cout << p << ", "; cout << endl;
            // cout << num << endl;
            res += num;
        }
        path.pop_back();
    }
    
    int sumRootToLeaf(TreeNode* root) {
        dfs(root);
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-root-to-leaf-binary-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-root-to-leaf-binary-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-root-to-leaf-binary-numbers/)