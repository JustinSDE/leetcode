# 687. Longest Univalue Path | 最长同值路径

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.</p>

<p><b>Note:</b> The length of path between two nodes is represented by the number of edges between them.</p>

<p>
<b>Example 1:</b>
</p>


<p>
Input:
<pre>
              5
             / \
            4   5
           / \   \
          1   1   5
</pre>
</p>

<p>
Output:
<pre>
2
</pre>
</p>

<p>
<b>Example 2:</b>
</p>


<p>
Input:
<pre>
              1
             / \
            4   5
           / \   \
          4   4   5
</pre>
</p>

<p>
Output:
<pre>
2
</pre>
</p>

<p><b>Note:</b>
The given binary tree has not more than 10000 nodes.  The height of the tree is not more than 1000.
</p> instead-->
<p>给定一个二叉树，找到最长的路径，这个路径中的每个节点具有相同值。 这条路径可以经过也可以不经过根节点。</p>

<p><strong>注意</strong>：两个节点之间的路径长度由它们之间的边数表示。</p>

<p><strong>示例 1:</strong></p>

<p>输入:</p>

<pre>
              5
             / \
            4   5
           / \   \
          1   1   5
</pre>

<p>输出:</p>

<pre>
2
</pre>

<p><strong>示例 2:</strong></p>

<p>输入:</p>

<pre>
              1
             / \
            4   5
           / \   \
          4   4   5
</pre>

<p>输出:</p>

<pre>
2
</pre>

<p><strong>注意:</strong> 给定的二叉树不超过10000个结点。&nbsp;树的高度不超过1000。</p>


## Note

这题虽然被归到了Easy难度，但其实难度还是蛮大的，不过也可能是我想复杂了。

经过根节点的最长同值路径：如果左孩子与根节点同值，取左子树的左最长同值路径和右最长同值路径的较大者+1；如果右孩子与根节点同值，取右子树的左最长同值路径和右最长同值路径的较大者+1。

为什么要计算左最长同值路径和右最长同值路径呢？因为经过节点的最长同值路径可能是从一侧跨过节点到另一侧，当该节点作为根节点的孩子时，从根节点出发，只能到该节点的左侧或右侧。


## Solution

Language: **cpp**  /  Runtime: 40 ms

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
    int max_len = 0;
    int longestLeftPath(TreeNode* root){
        if(!root || !root->left || root->val != root->left->val){
            return 0;
        }
        return 1 + max(longestLeftPath(root->left), longestRightPath(root->left));
    }
    int longestRightPath(TreeNode* root){
        if(!root || !root->right || root->val != root->right->val){
            return 0;
        }
        return 1 + max(longestLeftPath(root->right), longestRightPath(root->right));
    }
    int longestPath(TreeNode* root){
        if(!root){
            return 0;
        }
        int res = 0;
        if(root->left && root->val == root->left->val){
            res += 1 + max(longestLeftPath(root->left), longestRightPath(root->left));
        }
        if(root->right && root->val == root->right->val){
            res += 1 + max(longestLeftPath(root->right), longestRightPath(root->right));
        }
        return res;
    }
    void dfs(TreeNode* root){
        if(!root){
            return;
        }
        max_len = max(max_len, longestPath(root));
        if(root->left){
            dfs(root->left);
        }
        if(root->right){
            dfs(root->right);
        }
    }
    int longestUnivaluePath(TreeNode* root) {
        if(!root){
            return 0;
        }
        dfs(root);
        return max_len;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-univalue-path/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-univalue-path/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-univalue-path/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-univalue-path/)