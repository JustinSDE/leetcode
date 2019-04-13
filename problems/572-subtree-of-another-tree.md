# 572. Subtree of Another Tree | 另一个树的子树

## Question description

<!--If you want to use the English description, use <p>
Given two non-empty binary trees <b>s</b> and <b>t</b>, check whether tree <b>t</b> has exactly the same structure and node values with a subtree of <b>s</b>. A subtree of <b>s</b> is a tree consists of a node in <b>s</b> and all of this node's descendants. The tree <b>s</b> could also be considered as a subtree of itself.
</p>

<p><b>Example 1:</b><br>

Given tree s:
<pre>
     3
    / \
   4   5
  / \
 1   2
</pre>
Given tree t:
<pre>
   4 
  / \
 1   2
</pre>
Return <b>true</b>, because t has the same structure and node values with a subtree of s.
</p>

<p><b>Example 2:</b><br>

Given tree s:
<pre>
     3
    / \
   4   5
  / \
 1   2
    /
   0
</pre>
Given tree t:
<pre>
   4
  / \
 1   2
</pre>
Return <b>false</b>.
</p> instead-->
<p>给定两个非空二叉树 <strong>s</strong> 和 <strong>t</strong>，检验&nbsp;<strong>s</strong> 中是否包含和 <strong>t</strong> 具有相同结构和节点值的子树。<strong>s</strong> 的一个子树包括 <strong>s</strong> 的一个节点和这个节点的所有子孙。<strong>s</strong> 也可以看做它自身的一棵子树。</p>

<p><strong>示例 1:</strong><br />
给定的树 s:</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
</pre>

<p>给定的树 t：</p>

<pre>
   4 
  / \
 1   2
</pre>

<p>返回 <strong>true</strong>，因为 t 与 s 的一个子树拥有相同的结构和节点值。</p>

<p><strong>示例 2:</strong><br />
给定的树 s：</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
    /
   0
</pre>

<p>给定的树 t：</p>

<pre>
   4
  / \
 1   2
</pre>

<p>返回 <strong>false</strong>。</p>


## Note

这题有利于理解递归。判定两个树相同，就是判断根节点相同，且其子树相同，这是递归。判定树A是树B的子树，就是判断树A和树B是否相同，如果相同，则是子树；如果不同，就判断树B的子树是否有和树A相同的，这也是个递归的过程。

本题采用两个递归+空指针判断即可。


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
class Solution {
public:
    bool isSametree(TreeNode* t1, TreeNode* t2){
        if(!t1 && !t2){
            return true;
        }
        if(!t1 || !t2){
            return false;
        }
        if(t1->val == t2->val){
            return isSametree(t1->left, t2->left) && isSametree(t1->right, t2->right);
        }else{
            return false;
        }
    }
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if(!s && !t){
            return true;
        }
        if(!s || !t){
            return false;
        }
        if(isSametree(s, t)){
            return true;
        }
        return isSubtree(s->left, t) || isSubtree(s->right, t);
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/subtree-of-another-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subtree-of-another-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/subtree-of-another-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/subtree-of-another-tree/)