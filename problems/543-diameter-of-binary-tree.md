# 543. Diameter of Binary Tree | 二叉树的直径

## Question description

<!--If you want to use the English description, use <p>
Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the <b>longest</b> path between any two nodes in a tree. This path may or may not pass through the root.
</p>

<p>
<b>Example:</b><br />
Given a binary tree <br />
<pre>
          1
         / \
        2   3
       / \     
      4   5    
</pre>
</p>
<p>
Return <b>3</b>, which is the length of the path [4,2,1,3] or [5,2,1,3].
</p>

<p><b>Note:</b>
The length of path between two nodes is represented by the number of edges between them.
</p> instead-->
<p>给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过根结点。</p>

<p><strong>示例 :</strong><br />
给定二叉树</p>

<pre>
          1
         / \
        2   3
       / \     
      4   5    
</pre>

<p>返回&nbsp;<strong>3</strong>, 它的长度是路径 [4,2,1,3] 或者&nbsp;[5,2,1,3]。</p>

<p><strong>注意：</strong>两结点之间的路径长度是以它们之间边的数目表示。</p>




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
    vector<int> tmp;
    int maxDepth(TreeNode* node){
        if(!node){
            return 0;
        }
        int l = maxDepth(node->left);
        int r = maxDepth(node->right);
        tmp.push_back(l + r);
        return 1 + max(l, r);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(!root){
            return 0;
        }
        maxDepth(root);
        return *max_element(tmp.begin(), tmp.end());
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/diameter-of-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/diameter-of-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/diameter-of-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/diameter-of-binary-tree/)