# 129. Sum Root to Leaf Numbers | 求根到叶子节点数字之和

## Question description

<!--If you want to use the English description, use <p>Given a binary tree containing digits from <code>0-9</code> only, each root-to-leaf path could represent a number.</p>

<p>An example is the root-to-leaf path <code>1-&gt;2-&gt;3</code> which represents the number <code>123</code>.</p>

<p>Find the total sum of all root-to-leaf numbers.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3]
    1
   / \
  2   3
<strong>Output:</strong> 25
<strong>Explanation:</strong>
The root-to-leaf path <code>1-&gt;2</code> represents the number <code>12</code>.
The root-to-leaf path <code>1-&gt;3</code> represents the number <code>13</code>.
Therefore, sum = 12 + 13 = <code>25</code>.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,9,0,5,1]
    4
   / \
  9   0
&nbsp;/ \
5   1
<strong>Output:</strong> 1026
<strong>Explanation:</strong>
The root-to-leaf path <code>4-&gt;9-&gt;5</code> represents the number 495.
The root-to-leaf path <code>4-&gt;9-&gt;1</code> represents the number 491.
The root-to-leaf path <code>4-&gt;0</code> represents the number 40.
Therefore, sum = 495 + 491 + 40 = <code>1026</code>.</pre>
 instead-->
<p>给定一个二叉树，它的每个结点都存放一个&nbsp;<code>0-9</code>&nbsp;的数字，每条从根到叶子节点的路径都代表一个数字。</p>

<p>例如，从根到叶子节点路径 <code>1-&gt;2-&gt;3</code> 代表数字 <code>123</code>。</p>

<p>计算从根到叶子节点生成的所有数字之和。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
    1
   / \
  2   3
<strong>输出:</strong> 25
<strong>解释:</strong>
从根到叶子节点路径 <code>1-&gt;2</code> 代表数字 <code>12</code>.
从根到叶子节点路径 <code>1-&gt;3</code> 代表数字 <code>13</code>.
因此，数字总和 = 12 + 13 = <code>25</code>.</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [4,9,0,5,1]
    4
   / \
  9   0
&nbsp;/ \
5   1
<strong>输出:</strong> 1026
<strong>解释:</strong>
从根到叶子节点路径 <code>4-&gt;9-&gt;5</code> 代表数字 495.
从根到叶子节点路径 <code>4-&gt;9-&gt;1</code> 代表数字 491.
从根到叶子节点路径 <code>4-&gt;0</code> 代表数字 40.
因此，数字总和 = 495 + 491 + 40 = <code>1026</code>.</pre>




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
    int res = 0;
    void dfs(TreeNode* node, vector<int>& path) {
        if (!node) {
            return;
        }
        path.push_back(node->val);
        if (!node->left && !node->right) {
            int k = 0;
            for (int i : path) {
                k = 10 * k + i;
            }
            cout << k << endl;
            res += k;
        }
        if (node->left) {
            dfs(node->left, path);
        }
        if (node->right) {
            dfs(node->right, path);
        }
        path.pop_back();
    }

    int sumNumbers(TreeNode* root) {
        vector<int> path;
        dfs(root, path);
        return res;
    }
};

static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-root-to-leaf-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-root-to-leaf-numbers/)