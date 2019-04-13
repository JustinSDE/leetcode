# 92. Reverse Linked List II | 反转链表 II

## Question description

<!--If you want to use the English description, use <p>Reverse a linked list from position <em>m</em> to <em>n</em>. Do it in one-pass.</p>

<p><strong>Note:&nbsp;</strong>1 &le; <em>m</em> &le; <em>n</em> &le; length of list.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, <em>m</em> = 2, <em>n</em> = 4
<strong>Output:</strong> 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;NULL
</pre>
 instead-->
<p>反转从位置 <em>m</em> 到 <em>n</em> 的链表。请使用一趟扫描完成反转。</p>

<p><strong>说明:</strong><br>
1 &le;&nbsp;<em>m</em>&nbsp;&le;&nbsp;<em>n</em>&nbsp;&le; 链表长度。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, <em>m</em> = 2, <em>n</em> = 4
<strong>输出:</strong> 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;NULL</pre>




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
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        if (n == m) { return head; }
        ListNode* guard = new ListNode(0);
        guard->next = head;
        ListNode* st = guard;
        for (int i=0; i<m-1; ++i) {
            st = st->next;
        }
        ListNode* p = st;
        ListNode* q = p->next;
        ListNode* r = q->next;
        for (int i=0; i<n-m; ++i) {
            p = q;
            q = r;
            r = r->next;
            q->next = p;
        }
        st->next->next = r;
        st->next = q;
        return guard->next;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-linked-list-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-linked-list-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-linked-list-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-linked-list-ii/)