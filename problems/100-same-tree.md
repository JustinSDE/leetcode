# 100. Same Tree | 相同的树

## Question description

<!--If you want to use the English description, use <p>Given two binary trees, write a function to check if they are the same or not.</p>

<p>Two binary trees are considered the same if they are structurally identical and the nodes have the same value.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong>     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

<strong>Output:</strong> false
</pre>
 instead-->
<p>给定两个二叉树，编写一个函数来检验它们是否相同。</p>

<p>如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>      1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

<strong>输出:</strong> true</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:  </strong>    1          1
          /           \
         2             2

        [1,2],     [1,null,2]

<strong>输出:</strong> false
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong>       1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

<strong>输出:</strong> false
</pre>




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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(!p && !q) return true;
        if(!p || !q || p->val != q->val) return false;
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/same-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/same-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/same-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/same-tree/)