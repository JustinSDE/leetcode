# 230. Kth Smallest Element in a BST | 二叉搜索树中第K小的元素

## Question description

<!--If you want to use the English description, use <p>Given a binary search tree, write a function <code>kthSmallest</code> to find the <b>k</b>th smallest element in it.</p>

<p><b>Note: </b><br />
You may assume k is always valid, 1 &le; k &le; BST&#39;s total elements.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
&nbsp;  2
<strong>Output:</strong> 1</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
<strong>Output:</strong> 3
</pre>

<p><b>Follow up:</b><br />
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?</p>
 instead-->
<p>给定一个二叉搜索树，编写一个函数&nbsp;<code>kthSmallest</code>&nbsp;来查找其中第&nbsp;<strong>k&nbsp;</strong>个最小的元素。</p>

<p><strong>说明：</strong><br>
你可以假设 k 总是有效的，1 &le; k &le; 二叉搜索树元素个数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
&nbsp;  2
<strong>输出:</strong> 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
<strong>输出:</strong> 3</pre>

<p><strong>进阶：</strong><br>
如果二叉搜索树经常被修改（插入/删除操作）并且你需要频繁地查找第 k 小的值，你将如何优化&nbsp;<code>kthSmallest</code>&nbsp;函数？</p>




## Solution

Language: **cpp**  /  Runtime: 8 ms

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
    int* res = nullptr;
    int cnt = 1;

    int kthSmallest(TreeNode* root, int k) {
        if (root == NULL || k == 0) return NULL;
        if (!res) {
            kthSmallest(root->left, k);
        }
        if (!res) {
            if (cnt == k) {
                res = &(root->val);
            }
            cnt++;
        }
        if (!res) {
            kthSmallest(root->right, k);
        }

        if (res) {
            return *res;
        } else {
            return NULL;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/description/)

Solution: [LeetCode](https://leetcode.com/articles/kth-smallest-element-in-a-bst/)  /  [LeetCode中国](https://leetcode-cn.com/articles/kth-smallest-element-in-a-bst/)