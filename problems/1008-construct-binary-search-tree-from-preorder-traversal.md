# 1008. Construct Binary Search Tree from Preorder Traversal | 先序遍历构造二叉树

## Question description

<!--If you want to use the English description, use <p>Return the root node of a binary <strong>search</strong> tree that matches the given <code>preorder</code> traversal.</p>

<p><em>(Recall that a binary search tree&nbsp;is a binary tree where for every <font face="monospace">node</font>, any descendant of <code>node.left</code> has a value <code>&lt;</code>&nbsp;<code>node.val</code>, and any descendant of <code>node.right</code> has a value <code>&gt;</code>&nbsp;<code>node.val</code>.&nbsp; Also recall that a preorder traversal&nbsp;displays the value of the&nbsp;<code>node</code> first, then traverses <code>node.left</code>, then traverses <code>node.right</code>.)</em></p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[8,5,1,7,10,12]</span>
<strong>Output: </strong><span id="example-output-1">[8,5,10,1,7,null,12]
<img alt="" src="https://assets.leetcode.com/uploads/2019/03/06/1266.png" style="height: 200px; width: 306px;" /></span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong>&nbsp;</p>

<ol>
	<li><code>1 &lt;= preorder.length &lt;= 100</code></li>
	<li>The values of <code>preorder</code> are distinct.</li>
</ol>
 instead-->
<p>返回与给定先序遍历&nbsp;<code>preorder</code> 相匹配的二叉搜索树（binary <strong>search</strong> tree）的根结点。</p>

<p><em>(回想一下，二叉搜索树是二叉树的一种，其每个节点都满足以下规则，对于&nbsp;<code>node.left</code>&nbsp;的任何后代，值总 <code>&lt;</code> <code>node.val</code>，而 <code>node.right</code> 的任何后代，值总 <code>&gt;</code> <code>node.val</code>。此外，先序遍历首先显示节点的值，然后遍历 <code>node.left</code>，接着遍历 <code>node.right</code>。）</em></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[8,5,1,7,10,12]
<strong>输出：</strong>[8,5,10,1,7,null,12]
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/03/08/1266.png" style="height: 200px; width: 306px;">
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= preorder.length &lt;= 100</code></li>
	<li>先序&nbsp;<code>preorder</code>&nbsp;中的值是不同的。</li>
</ol>




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
    TreeNode* build(vector<int>& pre, int pst, int ped, vector<int>& in, int ist, int ied) {
        if (ped <= pst || ied <= ist || pst >= (int)pre.size()) 
            return NULL;
        TreeNode* root = new TreeNode(pre[pst]);
        int iroot = -1;
        for (int i = ist; i < ied; i++) {
            if (in[i] == pre[pst]) {
                iroot = i;
                break;
            }
        }
        root->left = build(pre, pst + 1, pst + 1 + iroot - ist, in, ist, iroot);
        root->right = build(pre, pst + 1 + iroot - ist, ped, in, iroot + 1, ied);
        return root;
    }

    TreeNode* bstFromPreorder(vector<int>& preorder) {
        vector<int> inorder(preorder);
        sort(inorder.begin(), inorder.end());
        if (!preorder.empty()) {
            return build(preorder, 0, preorder.size(), inorder, 0, inorder.size());
        } else {
            return NULL;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-binary-search-tree-from-preorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/construct-binary-search-tree-from-preorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/construct-binary-search-tree-from-preorder-traversal/)