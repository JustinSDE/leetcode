# 589. N-ary Tree Preorder Traversal | N叉树的前序遍历

## Question description

<!--If you want to use the English description, use <p>Given an n-ary tree, return the <i>preorder</i> traversal of its nodes&#39; values.</p>

<p>For example, given a <code>3-ary</code> tree:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>Return its preorder traversal as: <code>[1,3,5,6,2,4]</code>.</p>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<p>Recursive solution is trivial, could you do it iteratively?</p>
 instead-->
<p>给定一个 N 叉树，返回其节点值的<em>前序遍历</em>。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>返回其前序遍历: <code>[1,3,5,6,2,4]</code>。</p>

<p>&nbsp;</p>

<p><strong>说明:&nbsp;</strong>递归法很简单，你可以使用迭代法完成此题吗?</p>



## Solution

Language: **cpp**  /  Runtime: 80 ms

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
private:
    void preorderProcess(Node* cur, vector<int>& res){
        if(!cur) return;
        res.push_back(cur->val);
        for(Node* child : cur->children)
            preorderProcess(child, res);
    }
public:
    vector<int> preorder(Node* root) {
        vector<int> res;
        preorderProcess(root, res);
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/description/)

Solution: [LeetCode](https://leetcode.com/articles/n-ary-tree-preorder-traversal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/n-ary-tree-preorder-traversal/)