# 141. Linked List Cycle | 环形链表

## Question description

<!--If you want to use the English description, use <p>Given a linked list, determine if it has a cycle in it.</p>

<p>To represent a cycle in the given linked list, we use an integer <code>pos</code> which represents the position (0-indexed)&nbsp;in the linked list where tail connects to. If <code>pos</code> is <code>-1</code>, then there is no cycle in the linked list.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>head = <span id="example-input-1-1">[3,2,0,-4]</span>, pos = <span id="example-input-1-2">1</span>
<strong>Output: </strong><span id="example-output-1">true
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the second node.</span>
</pre>
</div>

<div>
<p><span><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png" style="width: 300px; height: 97px; margin-top: 8px; margin-bottom: 8px;" /></span></p>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>head = <span id="example-input-1-1">[1,2]</span>, pos = <span id="example-input-1-2">0</span>
<strong>Output: </strong><span id="example-output-1">true
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the first node.</span>
</pre>
</div>

<div>
<p><span><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png" style="width: 141px; height: 74px;" /></span></p>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>head = <span id="example-input-1-1">[1]</span>, pos = <span id="example-input-1-2">-1</span>
<strong>Output: </strong><span id="example-output-1">false
<strong>Explanation:</strong> There is no cycle in the linked list.</span>
</pre>
</div>

<p><span><img alt="" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png" style="width: 45px; height: 45px;" /></span></p>

<p>&nbsp;</p>

<p><strong>Follow up:</strong></p>

<p>Can you solve it using <em>O(1)</em> (i.e. constant) memory?</p>
 instead-->
<p>给定一个链表，判断链表中是否有环。</p>

<p>为了表示给定链表中的环，我们使用整数 <code>pos</code> 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 <code>pos</code> 是 <code>-1</code>，则在该链表中没有环。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>head = [3,2,0,-4], pos = 1
<strong>输出：</strong>true
<strong>解释：</strong>链表中有一个环，其尾部连接到第二个节点。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png" style="height: 97px; width: 300px;"></p>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>head = [1,2], pos = 0
<strong>输出：</strong>true
<strong>解释：</strong>链表中有一个环，其尾部连接到第一个节点。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png" style="height: 74px; width: 141px;"></p>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>head = [1], pos = -1
<strong>输出：</strong>false
<strong>解释：</strong>链表中没有环。
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png" style="height: 45px; width: 45px;"></p>

<p>&nbsp;</p>

<p><strong>进阶：</strong></p>

<p>你能用 <em>O(1)</em>（即，常量）内存解决此问题吗？</p>




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
    bool hasCycle(ListNode *head) {
        if (!head) return false;
        ListNode* p = head;
        ListNode* q = head;
        while (q && q->next) {
            q = q->next->next;
            p = p->next;
            if (p == q) return true;
        }
        return false;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/linked-list-cycle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/linked-list-cycle/description/)

Solution: [LeetCode](https://leetcode.com/articles/linked-list-cycle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/linked-list-cycle/)