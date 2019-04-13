# 203. Remove Linked List Elements | 移除链表元素

## Question description

<!--If you want to use the English description, use <p>Remove all elements from a linked list of integers that have value <b><i>val</i></b>.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b>  1-&gt;2-&gt;6-&gt;3-&gt;4-&gt;5-&gt;6, <em><b>val</b></em> = 6
<b>Output:</b> 1-&gt;2-&gt;3-&gt;4-&gt;5
</pre>
 instead-->
<p>删除链表中等于给定值&nbsp;<strong><em>val&nbsp;</em></strong>的所有节点。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;6-&gt;3-&gt;4-&gt;5-&gt;6, <em><strong>val</strong></em> = 6
<strong>输出:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5
</pre>




## Solution

Language: **cpp**  /  Runtime: 24 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* p = dummy;
        while (p->next) {
            if (p->next->val != val) {
                p = p->next;
            } else {
                ListNode* t = p->next;
                p->next = t->next;
                delete t;
            }
        }
        return dummy->next;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-linked-list-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-linked-list-elements/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-linked-list-elements/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-linked-list-elements/)