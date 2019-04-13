# 98. Validate Binary Search Tree | 验证二叉搜索树

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, determine if it is a valid binary search tree (BST).</p>

<p>Assume a BST is defined as follows:</p>

<ul>
	<li>The left subtree of a node contains only nodes with keys <strong>less than</strong> the node&#39;s key.</li>
	<li>The right subtree of a node contains only nodes with keys <strong>greater than</strong> the node&#39;s key.</li>
	<li>Both the left and right subtrees must also be binary search trees.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
    2
   / \
  1   3
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
    5
   / \
  1   4
&nbsp;    / \
&nbsp;   3   6
<strong>Output:</strong> false
<strong>Explanation:</strong> The input is: [5,1,4,null,null,3,6]. The root node&#39;s value
&nbsp;            is 5 but its right child&#39;s value is 4.
</pre>
 instead-->
<p>给定一个二叉树，判断其是否是一个有效的二叉搜索树。</p>

<p>假设一个二叉搜索树具有如下特征：</p>

<ul>
	<li>节点的左子树只包含<strong>小于</strong>当前节点的数。</li>
	<li>节点的右子树只包含<strong>大于</strong>当前节点的数。</li>
	<li>所有左子树和右子树自身必须也是二叉搜索树。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
    2
   / \
  1   3
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:
</strong>    5
   / \
  1   4
&nbsp;    / \
&nbsp;   3   6
<strong>输出:</strong> false
<strong>解释:</strong> 输入为: [5,1,4,null,null,3,6]。
&nbsp;    根节点的值为 5 ，但是其右子节点值为 4 。
</pre>


## Note

注意BST的定义，根节点比左子树所有节点大，比右子树所有节点小，而不是只和子节点比较。

BST重要性质：中序遍历数组是升序的。


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
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    void inorder(TreeNode* node, bool& res, int*& last) {
        if (!res) {
            return;
        }
        // cout << "[In] " << node->val << "  " << res << endl;
        if (node->left) {
            inorder(node->left, res, last);
        }

        if (last == nullptr || node->val > *last) {
            last = &(node->val);
        } else {
            res = false;
        }

        if (node->right) {
            inorder(node->right, res, last);
        }
        // cout << "[Out] " << node->val << "  " << res << endl;
    }

    bool isValidBST(TreeNode* root) {
        if (!root) { return true; }
        bool res = true;
        int* last = nullptr;
        inorder(root, res, last);
        // cout << "res: " << res << endl;
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/validate-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/validate-binary-search-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/validate-binary-search-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/validate-binary-search-tree/)