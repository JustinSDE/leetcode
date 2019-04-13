# 148. Sort List | 排序链表

## Question description

<!--If you want to use the English description, use <p>Sort a linked list in <em>O</em>(<em>n</em> log <em>n</em>) time using constant space complexity.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>Output:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>Output:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5</pre>
 instead-->
<p>在&nbsp;<em>O</em>(<em>n</em>&nbsp;log&nbsp;<em>n</em>) 时间复杂度和常数级空间复杂度下，对链表进行排序。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>输出:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>输出:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5</pre>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode sortList(ListNode head) {
        // 空节点或只有一个节点
        if (head == null || head.next == null) return head;
        // 只有两个节点
        if (head.next.next == null) {
            if (head.val > head.next.val) {
                ListNode p = head.next;
                head.next = null;
                p.next = head;
                head = p;
            }
            return head;
        }
        // 其余情况，分治
        ListNode p = head, q = head;
        while (q.next != null && q.next.next != null) {
            p = p.next;
            q = q.next.next;
        }
        ListNode rhead = p.next;
        p.next = null;
        ListNode l = sortList(head);
        ListNode r = sortList(rhead);
        // 归并
        ListNode dummy = new ListNode(-1);
        ListNode t = dummy;
        while (l != null || r != null) {
            if (l != null && r != null) {
                if (l.val > r.val) {
                    t.next = r;
                    r = r.next;
                } else {
                    t.next = l;
                    l = l.next; 
                }
                t = t.next;
                t.next = null;
            } else {
                t.next = l != null ? l : r;
                break;
            }
        }
        return dummy.next;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sort-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/sort-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sort-list/)