# 101. Symmetric Tree | 对称二叉树

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).</p>

<p>
For example, this binary tree <code>[1,2,2,3,4,4,3]</code> is symmetric:
<pre>
    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>
</p>
<p>
But the following <code>[1,2,2,null,3,null,3]</code>  is not:<br />
<pre>
    1
   / \
  2   2
   \   \
   3    3
</pre>
</p>

<p>
<b>Note:</b><br />
Bonus points if you could solve it both recursively and iteratively.
</p> instead-->
<p>给定一个二叉树，检查它是否是镜像对称的。</p>

<p>例如，二叉树&nbsp;<code>[1,2,2,3,4,4,3]</code> 是对称的。</p>

<pre>    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>

<p>但是下面这个&nbsp;<code>[1,2,2,null,3,null,3]</code> 则不是镜像对称的:</p>

<pre>    1
   / \
  2   2
   \   \
   3    3
</pre>

<p><strong>说明:</strong></p>

<p>如果你可以运用递归和迭代两种方法解决这个问题，会很加分。</p>




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
private:
    bool isSymmetricNode(TreeNode* left, TreeNode* right){
        if(!left && !right)
            return true;
        if(!left || !right || left->val != right->val)
            return false;
        return isSymmetricNode(left->left, right->right) && isSymmetricNode(left->right, right->left);
}
public:
    bool isSymmetric(TreeNode* root) {
        if(!root)
            return true;
        return isSymmetricNode(root->left, root->right);
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/symmetric-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/symmetric-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/symmetric-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/symmetric-tree/)