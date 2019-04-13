# 501. Find Mode in Binary Search Tree | 二叉搜索树中的众数

## Question description

<!--If you want to use the English description, use <p>Given a binary search tree (BST) with duplicates, find all the <a href="https://en.wikipedia.org/wiki/Mode_(statistics)" target="_blank">mode(s)</a> (the most frequently occurred element) in the given BST.</p>

<p>Assume a BST is defined as follows:</p>

<ul>
	<li>The left subtree of a node contains only nodes with keys <b>less than or equal to</b> the node&#39;s key.</li>
	<li>The right subtree of a node contains only nodes with keys <b>greater than or equal to</b> the node&#39;s key.</li>
	<li>Both the left and right subtrees must also be binary search trees.</li>
</ul>

<p>&nbsp;</p>

<p>For example:<br />
Given BST <code>[1,null,2,2]</code>,</p>

<pre>
   1
    \
     2
    /
   2
</pre>

<p>&nbsp;</p>

<p>return <code>[2]</code>.</p>

<p><b>Note:</b> If a tree has more than one mode, you can return them in any order.</p>

<p><b>Follow up:</b> Could you do that without using any extra space? (Assume that the implicit stack space incurred due to recursion does not count).</p>
 instead-->
<p>给定一个有相同值的二叉搜索树（BST），找出 BST 中的所有众数（出现频率最高的元素）。</p>

<p>假定 BST 有如下定义：</p>

<ul>
	<li>结点左子树中所含结点的值小于等于当前结点的值</li>
	<li>结点右子树中所含结点的值大于等于当前结点的值</li>
	<li>左子树和右子树都是二叉搜索树</li>
</ul>

<p>例如：<br>
给定 BST <code>[1,null,2,2]</code>,</p>

<pre>   1
    \
     2
    /
   2
</pre>

<p><code>返回[2]</code>.</p>

<p><strong>提示</strong>：如果众数超过1个，不需考虑输出顺序</p>

<p><strong>进阶：</strong>你可以不使用额外的空间吗？（假设由递归产生的隐式调用栈的开销不被计算在内）</p>


## Note

比较常规的思路：遍历树，进行频次统计，然后得到众数。没有利用题目是BST的特点，也使用了额外的空间。


## Solution

Language: **cpp**  /  Runtime: 20 ms

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
    unordered_map<int, int> cnt;
    void dfs(TreeNode* node){
        if(!node){
            return;
        }
        if(!cnt.count(node->val)){
            cnt[node->val] = 1;
        }else{
            cnt[node->val] += 1;
        }
        if(node->left){
            dfs(node->left);
        }
        if(node->right){
            dfs(node->right);
        }
    }
    vector<int> findMode(TreeNode* root) {
        vector<int> res;
        if(!root){
            return res;
        }
        dfs(root);
        vector<pair<int, int>> ccnt;
        for(auto item : cnt){
            ccnt.push_back(item);
        }
        if(ccnt.empty()){
            return res;
        }else{
            sort(ccnt.begin(), ccnt.end(), [](pair<int, int> a, pair<int, int> b){ return a.second > b.second; });
            int max_cnt = ccnt[0].second;
            for(auto item : ccnt){
                if(item.second == max_cnt){
                    res.push_back(item.first);
                }else{
                    break;
                }
            }
            return res;
        }
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-mode-in-binary-search-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-mode-in-binary-search-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-mode-in-binary-search-tree/)