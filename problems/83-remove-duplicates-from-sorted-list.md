# 83. Remove Duplicates from Sorted List | 删除排序链表中的重复元素

## Question description

<!--If you want to use the English description, use <p>Given a sorted linked list, delete all duplicates such that each element appear only <em>once</em>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;1-&gt;2
<strong>Output:</strong> 1-&gt;2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;3
<strong>Output:</strong> 1-&gt;2-&gt;3
</pre>
 instead-->
<p>给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;1-&gt;2
<strong>输出:</strong> 1-&gt;2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;3
<strong>输出:</strong> 1-&gt;2-&gt;3</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

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
        ListNode* p = head;
        ListNode* q = head->next;
        while (q) {
            if (p->val == q->val) {
                q = q->next;
                ListNode* tmp = p->next;
                p->next = q;
                delete tmp;
            } else {
                p = p->next;
                q = q->next;
            }
        }
        return head;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-duplicates-from-sorted-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-duplicates-from-sorted-list/)