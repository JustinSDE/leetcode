# 965. Univalued Binary Tree | 单值二叉树

## Question description

<!--If you want to use the English description, use <p>A binary tree is <em>univalued</em> if every node in the tree has the same value.</p>

<p>Return <code>true</code>&nbsp;if and only if the given tree is univalued.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2018/12/28/unival_bst_1.png" style="width: 265px; height: 172px;" />
<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,1,1,1,1,null,1]</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2018/12/28/unival_bst_2.png" style="width: 198px; height: 169px;" />
<pre>
<strong>Input: </strong><span id="example-input-2-1">[2,2,2,5,2]</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>
</div>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>The number of nodes in the given tree will be in the range <code>[1, 100]</code>.</li>
	<li>Each node&#39;s value will be an integer in the range <code>[0, 99]</code>.</li>
</ol>
 instead-->
<p>如果二叉树每个节点都具有相同的值，那么该二叉树就是<em>单值</em>二叉树。</p>

<p>只有给定的树是单值二叉树时，才返回&nbsp;<code>true</code>；否则返回 <code>false</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/29/screen-shot-2018-12-25-at-50104-pm.png" style="height: 159px; width: 200px;"></p>

<pre><strong>输入：</strong>[1,1,1,1,1,null,1]
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/29/screen-shot-2018-12-25-at-50050-pm.png" style="height: 158px; width: 200px;"></p>

<pre><strong>输入：</strong>[2,2,2,5,2]
<strong>输出：</strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>给定树的节点数范围是&nbsp;<code>[1, 100]</code>。</li>
	<li>每个节点的值都是整数，范围为&nbsp;<code>[0, 99]</code>&nbsp;。</li>
</ol>




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
    void dfs(TreeNode* node, int n, bool& res) {
        if (!res || !node) {
            return;
        }
        if (node->val != n) {
            res = false;
            return;
        }
        if (node->left) dfs(node->left, n, res);
        if (node->right) dfs(node->right, n, res);
    }

    bool isUnivalTree(TreeNode* root) {
        if (!root) return true;
        bool res = true;
        dfs(root, root->val, res);
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/univalued-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/univalued-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/univalued-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/univalued-binary-tree/)