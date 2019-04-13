# 328. Odd Even Linked List | 奇偶链表

## Question description

<!--If you want to use the English description, use <p>Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.</p>

<p>You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.</p>

<p><b>Example 1:</b></p>

<pre>
<strong>Input: </strong><code>1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL</code>
<strong>Output: </strong><code>1-&gt;3-&gt;5-&gt;2-&gt;4-&gt;NULL</code>
</pre>

<p><b>Example 2:</b></p>

<pre>
<strong>Input: </strong>2<code>-&gt;1-&gt;3-&gt;5-&gt;6-&gt;4-&gt;7-&gt;NULL</code>
<strong>Output: </strong><code>2-&gt;3-&gt;6-&gt;7-&gt;1-&gt;5-&gt;4-&gt;NULL</code>
</pre>

<p><b>Note:</b></p>

<ul>
	<li>The relative order inside both the even and odd groups should remain as it was in the input.</li>
	<li>The first node is considered odd, the second node even and so on ...</li>
</ul>
 instead-->
<p>给定一个单链表，把所有的奇数节点和偶数节点分别排在一起。请注意，这里的奇数节点和偶数节点指的是节点编号的奇偶性，而不是节点的值的奇偶性。</p>

<p>请尝试使用原地算法完成。你的算法的空间复杂度应为 O(1)，时间复杂度应为 O(nodes)，nodes 为节点总数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>输出:</strong> 1-&gt;3-&gt;5-&gt;2-&gt;4-&gt;NULL
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 2-&gt;1-&gt;3-&gt;5-&gt;6-&gt;4-&gt;7-&gt;NULL 
<strong>输出:</strong> 2-&gt;3-&gt;6-&gt;7-&gt;1-&gt;5-&gt;4-&gt;NULL</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>应当保持奇数节点和偶数节点的相对顺序。</li>
	<li>链表的第一个节点视为奇数节点，第二个节点视为偶数节点，以此类推。</li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 16 ms

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
    ListNode* oddEvenList(ListNode* head) {
        if (head == NULL || head->next == NULL) { return head; }
        ListNode* p = head;
        ListNode* qHead = head->next;
        ListNode* q = qHead;
        while (p->next && q->next) {
            p = p->next = q->next;
            q = q->next = p->next;
        }
        p->next = qHead;
        return head;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/odd-even-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/odd-even-linked-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/odd-even-linked-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/odd-even-linked-list/)