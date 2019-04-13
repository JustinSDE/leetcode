# 25. Reverse Nodes in k-Group | k个一组翻转链表

## Question description

<!--If you want to use the English description, use <p>Given a linked list, reverse the nodes of a linked list <em>k</em> at a time and return its modified list.</p>

<p><em>k</em> is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of <em>k</em> then left-out nodes in the end should remain as it is.</p>

<ul>
</ul>

<p><strong>Example:</strong></p>

<p>Given this linked list: <code>1-&gt;2-&gt;3-&gt;4-&gt;5</code></p>

<p>For <em>k</em> = 2, you should return: <code>2-&gt;1-&gt;4-&gt;3-&gt;5</code></p>

<p>For <em>k</em> = 3, you should return: <code>3-&gt;2-&gt;1-&gt;4-&gt;5</code></p>

<p><strong>Note:</strong></p>

<ul>
	<li>Only constant extra memory is allowed.</li>
	<li>You may not alter the values in the list&#39;s nodes, only nodes itself may be changed.</li>
</ul>
 instead-->
<p>给出一个链表，每&nbsp;<em>k&nbsp;</em>个节点一组进行翻转，并返回翻转后的链表。</p>

<p><em>k&nbsp;</em>是一个正整数，它的值小于或等于链表的长度。如果节点总数不是&nbsp;<em>k&nbsp;</em>的整数倍，那么将最后剩余节点保持原有顺序。</p>

<p><strong>示例 :</strong></p>

<p>给定这个链表：<code>1-&gt;2-&gt;3-&gt;4-&gt;5</code></p>

<p>当&nbsp;<em>k&nbsp;</em>= 2 时，应当返回: <code>2-&gt;1-&gt;4-&gt;3-&gt;5</code></p>

<p>当&nbsp;<em>k&nbsp;</em>= 3 时，应当返回: <code>3-&gt;2-&gt;1-&gt;4-&gt;5</code></p>

<p><strong>说明 :</strong></p>

<ul>
	<li>你的算法只能使用常数的额外空间。</li>
	<li><strong>你不能只是单纯的改变节点内部的值</strong>，而是需要实际的进行节点交换。</li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 36 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto _ = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        if (k == 1) { return head; }
        ListNode* guard = new ListNode(0);
        guard->next = head;
        ListNode* cur = guard;
        bool stop = false;
        while (!stop) {
            // to see whether need to reverse
            ListNode* tmp = cur;
            for(int i=0; i<k; ++i) {
                tmp = tmp->next;
                if (!tmp) {
                    stop = true;
                    break;
                }
            }
            if (!stop) {
                ListNode* p = cur;
                ListNode* q = cur;
                // loop swap for a batch reverse
                for (int i=k-1; i>0; --i) {
                    p = cur;
                    q = cur->next;
                    for (int j=0; j<i; ++j) {
                        // a->b->c->d  -->  a->c->b->d
                        p->next = q->next;
                        q->next = q->next->next;
                        p->next->next = q;
                        p = p->next;
                    }
                }
                // point to next batch
                for (int i=0; i<k; ++i) {
                    cur = cur->next;
                }
            }
        }
        return guard->next;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-nodes-in-k-group/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-nodes-in-k-group/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-nodes-in-k-group/)