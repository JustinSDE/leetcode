# 199. Binary Tree Right Side View | 二叉树的右视图

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, imagine yourself standing on the <em>right</em> side of it, return the values of the nodes you can see ordered from top to bottom.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;[1,2,3,null,5,null,4]
<strong>Output:</strong>&nbsp;[1, 3, 4]
<strong>Explanation:
</strong>
   1            &lt;---
 /   \
2     3         &lt;---
 \     \
  5     4       &lt;---
</pre> instead-->
<p>给定一棵二叉树，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;[1,2,3,null,5,null,4]
<strong>输出:</strong>&nbsp;[1, 3, 4]
<strong>解释:
</strong>
   1            &lt;---
 /   \
2     3         &lt;---
 \     \
  5     4       &lt;---
</pre>




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
public:
    vector<int> rightSideView(TreeNode* root) {
        vector<int> res;
        if (!root) return res;
        queue<TreeNode*> Q;
        Q.push(root);
        while (!Q.empty()) {
            int n = Q.size();
            while (n--) {
                auto t = Q.front();
                if (n == 0) res.push_back(t->val);
                Q.pop();
                if (t->left) Q.push(t->left);
                if (t->right) Q.push(t->right);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-tree-right-side-view/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-right-side-view/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-tree-right-side-view/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-tree-right-side-view/)