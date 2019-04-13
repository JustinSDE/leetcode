# 559. Maximum Depth of N-ary Tree | N叉树的最大深度

## Question description

<!--If you want to use the English description, use <p>Given a n-ary tree, find its maximum depth.</p>

<p>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p>For example, given a <code>3-ary</code> tree:</p>
&nbsp;

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>We should return its max depth, which is 3.</p>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The depth of the tree is at most <code>1000</code>.</li>
	<li>The total number of nodes is at most <code>5000</code>.</li>
</ol>
 instead-->
<p>给定一个 N 叉树，找到其最大深度。</p>

<p>最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>我们应返回其最大深度，3。</p>

<p><strong>说明:</strong></p>

<ol>
	<li>树的深度不会超过&nbsp;<code>1000</code>。</li>
	<li>树的节点总不会超过&nbsp;<code>5000</code>。</li>
</ol>

## Note

递归地计算一个节点的左右子树的树高，将高度设值为两个孩子最大高度加1。


## Solution

Language: **cpp**  /  Runtime: 92 ms

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/
class Solution {

public:
    int maxDepth(Node* root) {
        if(!root) return 0;
        int h = 0;
        for(Node* child : root->children){
            h = max(h, maxDepth(child));
        }
        return h + 1;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-depth-of-n-ary-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-depth-of-n-ary-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-depth-of-n-ary-tree/)