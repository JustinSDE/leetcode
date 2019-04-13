# 109. Convert Sorted List to Binary Search Tree | 有序链表转换二叉搜索树

## Question description

<!--If you want to use the English description, use <p>Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.</p>

<p>For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of <em>every</em> node never differ by more than 1.</p>

<p><strong>Example:</strong></p>

<pre>
Given the sorted linked list: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
</pre>
 instead-->
<p>给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。</p>

<p>本题中，一个高度平衡二叉树是指一个二叉树<em>每个节点&nbsp;</em>的左右两个子树的高度差的绝对值不超过 1。</p>

<p><strong>示例:</strong></p>

<pre>给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：

      0
     / \
   -3   9
   /   /
 -10  5
</pre>




## Solution

Language: **cpp**  /  Runtime: 20 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    void build(TreeNode*& ret, int st, int ed) {
        if (st > ed) return;
        if (st == ed) {
            ret = new TreeNode(0);
            return;
        }
        int mid = (st + ed) / 2;
        ret = new TreeNode(0);
        build(ret->left, st, mid-1);
        build(ret->right, mid+1, ed);
    }

    void inorder(TreeNode*& ret, ListNode*& cur) {
        if (!cur) return;
        if (ret->left) {
            inorder(ret->left, cur);
        }
        ret->val = cur->val;
        cur = cur->next;
        if (ret->right) {
            inorder(ret->right, cur);
        }
    }

    TreeNode* sortedListToBST(ListNode* head) {
        if (!head) return nullptr;
        int n = 0;
        ListNode* p = head;
        while (p) {
            n++;
            p = p->next;
        }
        TreeNode* ret = nullptr;
        build(ret, 0, n-1);  // build a tree and assign initial values
        inorder(ret, head);  // inorder traversal and assign values
        return ret;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/convert-sorted-list-to-binary-search-tree/description/)

Solution: [LeetCode](https://leetcode.com/articles/convert-sorted-list-to-binary-search-tree/)  /  [LeetCode中国](https://leetcode-cn.com/articles/convert-sorted-list-to-binary-search-tree/)