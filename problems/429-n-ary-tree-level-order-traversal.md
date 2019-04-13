# 429. N-ary Tree Level Order Traversal | N叉树的层序遍历

## Question description

<!--If you want to use the English description, use <p>Given an n-ary tree, return the level order traversal of its nodes&#39; values. (ie, from left to right, level by level).</p>

<p>For example, given a <code>3-ary</code> tree:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>We should return its level order traversal:</p>

<pre>
[
     [1],
     [3,2,4],
     [5,6]
]
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The depth of the tree is at most <code>1000</code>.</li>
	<li>The total number of nodes is at most <code>5000</code>.</li>
</ol>
 instead-->
<p>给定一个 N 叉树，返回其节点值的<em>层序遍历</em>。 (即从左到右，逐层遍历)。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>返回其层序遍历:</p>

<pre>[
     [1],
     [3,2,4],
     [5,6]
]
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ol>
	<li>树的深度不会超过&nbsp;<code>1000</code>。</li>
	<li>树的节点总数不会超过&nbsp;<code>5000</code>。</li>
</ol>



## Solution

Language: **cpp**  /  Runtime: 60 ms

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val = NULL;
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
    vector<vector<int>> levelOrder(Node* root) {
        vector<vector<int>> res;
        if(!root){
            return res;
        }
        queue<Node*> seq;
        set<Node*> vt;
        vt.insert(root);
        seq.push(root);
        vector<int> row;
        row.push_back(root->val);
        res.push_back(row);
        while(!seq.empty()){
            int n = seq.size();
            vector<int> row;
            while(n--){
                Node* tmp = seq.front();
                seq.pop();
                for(Node* child : tmp->children){
                    if(!vt.count(child)){
                        vt.insert(child);
                        seq.push(child);
                        row.push_back(child->val);
                    }
                }
            }
            if(!row.empty()){
                res.push_back(row);
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-ary-tree-level-order-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/n-ary-tree-level-order-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/n-ary-tree-level-order-traversal/)