# 222. Count Complete Tree Nodes | 完全二叉树的节点个数

## Question description

<!--If you want to use the English description, use <p>Given a <b>complete</b> binary tree, count the number of nodes.</p>

<p><b>Note: </b></p>

<p><b><u>Definition of a complete binary tree from <a href="http://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees" target="_blank">Wikipedia</a>:</u></b><br />
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2<sup>h</sup> nodes inclusive at the last level h.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 
    1
   / \
  2   3
 / \  /
4  5 6

<strong>Output:</strong> 6</pre>
 instead-->
<p>给出一个<strong>完全二叉树</strong>，求出该树的节点个数。</p>

<p><strong>说明：</strong></p>

<p><a href="https://baike.baidu.com/item/%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91/7773232?fr=aladdin">完全二叉树</a>的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~&nbsp;2<sup>h</sup>&nbsp;个节点。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 
    1
   / \
  2   3
 / \  /
4  5 6

<strong>输出:</strong> 6</pre>




## Solution

Language: **cpp**  /  Runtime: 36 ms

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
    int countNodes(TreeNode* root) {
        if (!root) return 0;
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-complete-tree-nodes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-complete-tree-nodes/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-complete-tree-nodes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-complete-tree-nodes/)