# 95. Unique Binary Search Trees II | 不同的二叉搜索树 II

## Question description

<!--If you want to use the English description, use <p>Given an integer <em>n</em>, generate all structurally unique <strong>BST&#39;s</strong> (binary search trees) that store values 1 ...&nbsp;<em>n</em>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong>
[
&nbsp; [1,null,3,2],
&nbsp; [3,2,null,1],
&nbsp; [3,1,null,null,2],
&nbsp; [2,1,3],
&nbsp; [1,null,2,null,3]
]
<strong>Explanation:</strong>
The above output corresponds to the 5 unique BST&#39;s shown below:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
</pre>
 instead-->
<p>给定一个整数 <em>n</em>，生成所有由 1 ...&nbsp;<em>n</em> 为节点所组成的<strong>二叉搜索树</strong>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong>
[
&nbsp; [1,null,3,2],
&nbsp; [3,2,null,1],
&nbsp; [3,1,null,null,2],
&nbsp; [2,1,3],
&nbsp; [1,null,2,null,3]
]
<strong>解释:</strong>
以上的输出对应以下 5 种不同结构的二叉搜索树：

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
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
    void backTracking(int l, int r, vector<TreeNode*>& ret) {
        if (l > r) {
            ret.emplace_back(nullptr);
            return;
        }
        if (l == r) {
            TreeNode* tmp = new TreeNode(l);
            ret.emplace_back(tmp);
            return;
        }
        for (int m=l; m<=r; ++m) {
            vector<TreeNode*> left;
            backTracking(l, m-1, left);
            vector<TreeNode*> right;
            backTracking(m+1, r, right);
            for (auto lt : left) {
                for (auto rt : right) {
                    TreeNode* root = new TreeNode(m);
                    root->left = lt;
                    root->right = rt;
                    ret.emplace_back(root);
                }
            }
        }
    }
    
    vector<TreeNode*> generateTrees(int n) {
        vector<TreeNode*> ret;
        if (n == 0) { return ret; }
        backTracking(1, n, ret);
        return ret;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/unique-binary-search-trees-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-binary-search-trees-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/unique-binary-search-trees-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/unique-binary-search-trees-ii/)