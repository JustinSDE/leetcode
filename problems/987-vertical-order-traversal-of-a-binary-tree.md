# 987. Vertical Order Traversal of a Binary Tree | 二叉树的垂序遍历

## Question description

<!--If you want to use the English description, use <p>Given a binary tree, return the <em>vertical order</em> traversal of its nodes&nbsp;values.</p>

<p>For each node at position <code>(X, Y)</code>, its left and right children respectively&nbsp;will be at positions <code>(X-1, Y-1)</code> and <code>(X+1, Y-1)</code>.</p>

<p>Running a vertical line from <code>X = -infinity</code> to <code>X = +infinity</code>, whenever the vertical line touches some nodes, we report the values of the nodes in order from top to bottom (decreasing <code>Y</code> coordinates).</p>

<p>If two nodes have the same position, then the value of the node that is reported first is the value that is smaller.</p>

<p>Return an list&nbsp;of non-empty reports in order of <code>X</code> coordinate.&nbsp; Every report will have a list of values of nodes.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/01/31/1236_example_1.PNG" style="width: 201px; height: 186px;" /></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">[3,9,20,null,null,15,7]</span>
<strong>Output: </strong><span id="example-output-1">[[9],[3,15],[20],[7]]</span>
<strong>Explanation: </strong>
Without loss of generality, we can assume the root node is at position (0, 0):
Then, the node with value 9 occurs at position (-1, -1);
The nodes with values 3 and 15 occur at positions (0, 0) and (0, -2);
The node with value 20 occurs at position (1, -1);
The node with value 7 occurs at position (2, -2).
</pre>

<div>
<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/01/31/tree2.png" style="width: 236px; height: 150px;" /></strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,3,4,5,6,7]</span>
<strong>Output: </strong><span id="example-output-2">[[4],[2],[1,5,6],[3],[7]]</span>
<strong>Explanation: </strong>
The node with value 5 and the node with value 6 have the same position according to the given scheme.
However, in the report &quot;[1,5,6]&quot;, the node value of 5 comes first since 5 is smaller than 6.
</pre>

<p>&nbsp;</p>
</div>

<p><strong>Note:</strong></p>

<ol>
	<li>The tree will have between <font face="monospace">1</font>&nbsp;and <code>1000</code> nodes.</li>
	<li>Each node&#39;s value will be between <code>0</code> and <code>1000</code>.</li>
</ol>
</div>

<div>
<div>&nbsp;</div>
</div>
 instead-->
<p>给定二叉树，按<em>垂序</em>遍历返回其结点值。</p>

<p>对位于&nbsp;<code>(X, Y)</code>&nbsp;的每个结点而言，其左右子结点分别位于&nbsp;<code>(X-1, Y-1)</code>&nbsp;和&nbsp;<code>(X+1, Y-1)</code>。</p>

<p>把一条垂线从&nbsp;<code>X = -infinity</code>&nbsp;移动到&nbsp;<code>X = +infinity</code>&nbsp;，每当该垂线与结点接触时，我们按从上到下的顺序报告结点的值（ <code>Y</code>&nbsp;坐标递减）。</p>

<p>如果两个结点位置相同，则首先报告的结点值较小。</p>

<p>按&nbsp;<code>X</code>&nbsp;坐标顺序返回非空报告的列表。每个报告都有一个结点值列表。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/02/1236_example_1.PNG" style="height: 186px; width: 201px;"></p>

<pre><strong>输入：</strong>[3,9,20,null,null,15,7]
<strong>输出：</strong>[[9],[3,15],[20],[7]]
<strong>解释： </strong>
在不丧失其普遍性的情况下，我们可以假设根结点位于 (0, 0)：
然后，值为 9 的结点出现在 (-1, -1)；
值为 3 和 15 的两个结点分别出现在 (0, 0) 和 (0, -2)；
值为 20 的结点出现在 (1, -1)；
值为 7 的结点出现在 (2, -2)。
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/tree2.png" style="height: 150px; width: 236px;"></strong></p>

<pre><strong>输入：</strong>[1,2,3,4,5,6,7]
<strong>输出：</strong>[[4],[2],[1,5,6],[3],[7]]
<strong>解释：</strong>
根据给定的方案，值为 5 和 6 的两个结点出现在同一位置。
然而，在报告 &quot;[1,5,6]&quot; 中，结点值 5 排在前面，因为 5 小于 6。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>树的结点数介于 <code>1</code>&nbsp;和&nbsp;<code>1000</code>&nbsp;之间。</li>
	<li>每个结点值介于&nbsp;<code>0</code>&nbsp;和&nbsp;<code>1000</code>&nbsp;之间。</li>
</ol>




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
struct TNI {
    TreeNode* node;
    int x;
    int y;
    TNI(TreeNode* node, int x, int y) : node(node), x(x), y(y) {}
};

class Solution {
public:
    vector<TNI*> info;
    void dfs(TNI* t) {
        if (!t->node) return;
        info.push_back(t);
        if (t->node->left) {
            TNI* tmp = new TNI(t->node->left, t->x - 1, t->y - 1);
            dfs(tmp);
        }
        if (t->node->right) {
            TNI* tmp = new TNI(t->node->right, t->x + 1, t->y - 1);
            dfs(tmp);
        }
    }
    
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        vector<vector<int> > res;
        if (!root) return res;
        TNI* r = new TNI(root, 0, 0);
        dfs(r);
        sort(info.begin(), info.end(), [](TNI* t1, TNI* t2) {
           if (t1->x != t2->x) {
               return t1->x < t2->x;
           } else if(t1->y != t2->y) {
               return t2->y < t1->y;
           } else {
               return t1->node->val < t2->node->val;
           }
        });
        int pre = INT_MIN;
        for (auto i : info) {
            if (i->x != pre) {
                res.push_back(vector<int>());
                pre = i->x;
            }
            res.back().push_back(i->node->val);
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/vertical-order-traversal-of-a-binary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/vertical-order-traversal-of-a-binary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/vertical-order-traversal-of-a-binary-tree/)