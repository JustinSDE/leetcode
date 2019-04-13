# 142. Linked List Cycle II | 环形链表 II

## Question description

<!--If you want to use the English description, use <p>Given a linked list, return the node where the cycle begins. If there is no cycle, return <code>null</code>.</p>

<p>To represent a cycle in the given linked list, we use an integer <code>pos</code> which represents the position (0-indexed)&nbsp;in the linked list where tail connects to. If <code>pos</code> is <code>-1</code>, then there is no cycle in the linked list.</p>

<p><b>Note:</b> Do not modify the linked list.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>head = [3,2,0,-4], pos = 1
<strong>Output: </strong>tail connects to node index 1
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the second node.
</pre>

<p><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png" style="height: 97px; width: 300px;" /></p>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>head = [1,2], pos = 0
<strong>Output: </strong>tail connects to node index 0
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the first node.
</pre>

<p><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png" style="height: 74px; width: 141px;" /></p>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>head = [1], pos = -1
<strong>Output: </strong>no cycle
<strong>Explanation:</strong> There is no cycle in the linked list.
</pre>

<p><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png" style="height: 45px; width: 45px;" /></p>

<p>&nbsp;</p>

<p><b>Follow up</b>:<br />
Can you solve it without using extra space?</p>
 instead-->
<p>给定一个链表，返回链表开始入环的第一个节点。&nbsp;如果链表无环，则返回&nbsp;<code>null</code>。</p>

<p>为了表示给定链表中的环，我们使用整数 <code>pos</code> 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 <code>pos</code> 是 <code>-1</code>，则在该链表中没有环。</p>

<p><strong>说明：</strong>不允许修改给定的链表。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>head = [3,2,0,-4], pos = 1
<strong>输出：</strong>tail connects to node index 1
<strong>解释：</strong>链表中有一个环，其尾部连接到第二个节点。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png" style="height: 97px; width: 300px;"></p>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>head = [1,2], pos = 0
<strong>输出：</strong>tail connects to node index 0
<strong>解释：</strong>链表中有一个环，其尾部连接到第一个节点。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png" style="height: 74px; width: 141px;"></p>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>head = [1], pos = -1
<strong>输出：</strong>no cycle
<strong>解释：</strong>链表中没有环。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png" style="height: 45px; width: 45px;"></p>

<p>&nbsp;</p>

<p><strong>进阶：</strong><br>
你是否可以不用额外空间解决此题？</p>




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
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        if (!head) return NULL;
        ListNode* p = head;
        ListNode* q = head;
        while (q && q->next) {
            q = q->next->next;
            p = p->next;
            if (p == q) {
                p = head;
                while (p != q) {
                    p = p->next;
                    q = q->next;
                }
                return p;
            }
        }
        return NULL;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/linked-list-cycle-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/linked-list-cycle-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/linked-list-cycle-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/linked-list-cycle-ii/)