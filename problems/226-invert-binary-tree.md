# 226. Invert Binary Tree | 翻转二叉树

## Question description

<!--If you want to use the English description, use <p>Invert a binary tree.</p>

<p><strong>Example:</strong></p>

<p>Input:</p>

<pre>
     4
   /   \
  2     7
 / \   / \
1   3 6   9</pre>

<p>Output:</p>

<pre>
     4
   /   \
  7     2
 / \   / \
9   6 3   1</pre>

<p><strong>Trivia:</strong><br />
This problem was inspired by <a href="https://twitter.com/mxcl/status/608682016205344768" target="_blank">this original tweet</a> by <a href="https://twitter.com/mxcl" target="_blank">Max Howell</a>:</p>

<blockquote>Google: 90% of our engineers use the software you wrote (Homebrew), but you can&rsquo;t invert a binary tree on a whiteboard so f*** off.</blockquote>
 instead-->
<p>翻转一棵二叉树。</p>

<p><strong>示例：</strong></p>

<p>输入：</p>

<pre>     4
   /   \
  2     7
 / \   / \
1   3 6   9</pre>

<p>输出：</p>

<pre>     4
   /   \
  7     2
 / \   / \
9   6 3   1</pre>

<p><strong>备注:</strong><br>
这个问题是受到 <a href="https://twitter.com/mxcl" target="_blank">Max Howell </a>的 <a href="https://twitter.com/mxcl/status/608682016205344768" target="_blank">原问题</a> 启发的 ：</p>

<blockquote>谷歌：我们90％的工程师使用您编写的软件(Homebrew)，但是您却无法在面试时在白板上写出翻转二叉树这道题，这太糟糕了。</blockquote>




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
    TreeNode* invertTree(TreeNode* root) {
        if(!root){
            return root;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> visit;
        visit.insert(root);
        seq.push(root);
        while(!seq.empty()){
            TreeNode* tmp = seq.front();
            seq.pop();
            swap(tmp->left, tmp->right);
            if(tmp->left && !visit.count(tmp->left)){
                visit.insert(tmp->left);
                seq.push(tmp->left);
            }
            if(tmp->right && !visit.count(tmp->right)){
                visit.insert(tmp->right);
                seq.push(tmp->right);
            }
        }
        return root;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/invert-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/invert-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/invert-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/invert-binary-tree/)