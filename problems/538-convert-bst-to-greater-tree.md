# 538. Convert BST to Greater Tree | 把二叉搜索树转换为累加树

## Question description

<!--If you want to use the English description, use <p>Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.</p>

<p>
<b>Example:</b>
<pre>
<b>Input:</b> The root of a Binary Search Tree like this:
              5
            /   \
           2     13

<b>Output:</b> The root of a Greater Tree like this:
             18
            /   \
          20     13
</pre>
</p> instead-->
<p>给定一个二叉搜索树（Binary Search Tree），把它转换成为累加树（Greater Tree)，使得每个节点的值是原来的节点值加上所有大于它的节点值之和。</p>

<p><strong>例如：</strong></p>

<pre>
<strong>输入:</strong> 二叉搜索树:
              5
            /   \
           2     13

<strong>输出:</strong> 转换为累加树:
             18
            /   \
          20     13
</pre>




## Solution

Language: **cpp**  /  Runtime: 24 ms

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
    int tmp = 0;
    void dfs(TreeNode* node){
        if(!node){
            return;
        }
        if(node->right){
            dfs(node->right);
        }
        node->val += tmp;
        tmp = node->val;
        if(node->left){
            dfs(node->left);
        }
    }
    TreeNode* convertBST(TreeNode* root) {
        dfs(root);
        return root;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/convert-bst-to-greater-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/convert-bst-to-greater-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/convert-bst-to-greater-tree/)