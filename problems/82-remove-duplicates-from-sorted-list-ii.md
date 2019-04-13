# 82. Remove Duplicates from Sorted List II | 删除排序链表中的重复元素 II

## Question description

<!--If you want to use the English description, use <p>Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only <em>distinct</em> numbers from the original list.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;3-&gt;4-&gt;4-&gt;5
<strong>Output:</strong> 1-&gt;2-&gt;5
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;1-&gt;1-&gt;2-&gt;3
<strong>Output:</strong> 2-&gt;3
</pre>
 instead-->
<p>给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中&nbsp;<em>没有重复出现&nbsp;</em>的数字。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;3-&gt;4-&gt;4-&gt;5
<strong>输出:</strong> 1-&gt;2-&gt;5
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 1-&gt;1-&gt;1-&gt;2-&gt;3
<strong>输出:</strong> 2-&gt;3</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head || !head->next) { return head; }
        ListNode* g = new ListNode(0);
        g->next = head;
        ListNode* p = g;
        ListNode* q = head->next;
        while (q) {
            if (q->val == p->next->val) {
                q = q->next;
            } else {
                if (p->next->next != q) {
                    p->next = q;
                } else {
                    p = p->next;
                }
                q = q->next;
            }
        }
        if (p->next->next != q) {
            p->next = q;
        }
        return g->next;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-duplicates-from-sorted-list-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-duplicates-from-sorted-list-ii/)