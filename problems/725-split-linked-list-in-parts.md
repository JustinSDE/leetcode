# 725. Split Linked List in Parts | 分隔链表

## Question description

<!--If you want to use the English description, use <p>Given a (singly) linked list with head node <code>root</code>, write a function to split the linked list into <code>k</code> consecutive linked list "parts".
</p><p>
The length of each part should be as equal as possible: no two parts should have a size differing by more than 1.  This may lead to some parts being null.
</p><p>
The parts should be in order of occurrence in the input list, and parts occurring earlier should always have a size greater than or equal parts occurring later.
</p><p>
Return a List of ListNode's representing the linked list parts that are formed.
</p>

Examples
1->2->3->4, k = 5 // 5 equal parts
[ [1], 
[2],
[3],
[4],
null ]

<p><b>Example 1:</b><br />
<pre style="white-space: pre-line">
<b>Input:</b> 
root = [1, 2, 3], k = 5
<b>Output:</b> [[1],[2],[3],[],[]]
<b>Explanation:</b>
The input and each element of the output are ListNodes, not arrays.
For example, the input root has root.val = 1, root.next.val = 2, \root.next.next.val = 3, and root.next.next.next = null.
The first element output[0] has output[0].val = 1, output[0].next = null.
The last element output[4] is null, but it's string representation as a ListNode is [].
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> 
root = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], k = 3
<b>Output:</b> [[1, 2, 3, 4], [5, 6, 7], [8, 9, 10]]
<b>Explanation:</b>
The input has been split into consecutive parts with size difference at most 1, and earlier parts are a larger size than the later parts.
</pre>
</p>

<p><b>Note:</b>
<li>The length of <code>root</code> will be in the range <code>[0, 1000]</code>.</li>
<li>Each value of a node in the input will be an integer in the range <code>[0, 999]</code>.</li>
<li><code>k</code> will be an integer in the range <code>[1, 50]</code>.</li>
</p> instead-->
<p>给定一个头结点为 <code>root</code> 的链表, 编写一个函数以将链表分隔为 <code>k</code> 个连续的部分。</p>

<p>每部分的长度应该尽可能的相等: 任意两部分的长度差距不能超过 1，也就是说可能有些部分为 null。</p>

<p>这k个部分应该按照在链表中出现的顺序进行输出，并且排在前面的部分的长度应该大于或等于后面的长度。</p>

<p>返回一个符合上述规则的链表的列表。</p>

<p>举例： 1-&gt;2-&gt;3-&gt;4, k = 5 // 5 结果 [ [1], [2], [3], [4], null ]</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> 
root = [1, 2, 3], k = 5
<strong>输出:</strong> [[1],[2],[3],[],[]]
<strong>解释:</strong>
输入输出各部分都应该是链表，而不是数组。
例如, 输入的结点 root 的 val= 1, root.next.val = 2, \root.next.next.val = 3, 且 root.next.next.next = null。
第一个输出 output[0] 是 output[0].val = 1, output[0].next = null。
最后一个元素 output[4] 为 null, 它代表了最后一个部分为空链表。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入:</strong> 
root = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], k = 3
<strong>输出:</strong> [[1, 2, 3, 4], [5, 6, 7], [8, 9, 10]]
<strong>解释:</strong>
输入被分成了几个连续的部分，并且每部分的长度相差不超过1.前面部分的长度大于等于后面部分的长度。
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>root</code> 的长度范围：&nbsp;<code>[0, 1000]</code>.</li>
	<li>输入的每个节点的大小范围：<code>[0, 999]</code>.</li>
	<li><code>k</code>&nbsp;的取值范围：&nbsp;<code>[1, 50]</code>.</li>
</ul>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 0 ms

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
    public ListNode[] splitListToParts(ListNode root, int k) {
        int n = 0;
        ListNode p = root;
        ListNode[] res = new ListNode[k];
        // 计算链表长度
        while (p != null) {
            n++;
            p = p.next;
        }
        // 计算每一份的长度
        int x = n / k;
        int[] nums = new int[k];
        for (int i = k - 1; i >= 0; i--) {
            nums[i] = x;
            if (n - x * (k - i) == i * (x + 1)) {
                x++;
            }
        }
        // for (int num : nums) System.out.print(num + " "); System.out.println();
        // 分割链表
        p = root;
        int idx = 0, cnt = 0;
        ListNode dummy = new ListNode(-1), t = null;
        while (p != null) {
            if (cnt == 0) {
                t = dummy;
            }
            t.next = p;
            p = p.next;
            t.next.next = null;
            t = t.next;
            cnt++;
            if (cnt == nums[idx]) {
                res[idx++] = dummy.next;
                dummy.next = null;
                cnt = 0;
            }
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/split-linked-list-in-parts/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/split-linked-list-in-parts/description/)

Solution: [LeetCode](https://leetcode.com/articles/split-linked-list-in-parts/)  /  [LeetCode中国](https://leetcode-cn.com/articles/split-linked-list-in-parts/)