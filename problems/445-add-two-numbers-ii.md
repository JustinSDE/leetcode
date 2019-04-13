# 445. Add Two Numbers II | 两数相加 II

## Question description

<!--If you want to use the English description, use <p>You are given two <b>non-empty</b> linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p><b>Follow up:</b><br />
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.
</p>

<p>
<b>Example:</b>
<pre>
<b>Input:</b> (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
<b>Output:</b> 7 -> 8 -> 0 -> 7
</pre>
</p> instead-->
<p>给定两个<strong>非空</strong>链表来代表两个非负整数。数字最高位位于链表开始位置。它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。</p>

<p>&nbsp;</p>

<p>你可以假设除了数字 0 之外，这两个数字都不会以零开头。</p>

<p><strong>进阶:</strong></p>

<p>如果输入链表不能修改该如何处理？换句话说，你不能对列表中的节点进行翻转。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong> (7 -&gt; 2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<strong>输出:</strong> 7 -&gt; 8 -&gt; 0 -&gt; 7
</pre>




## Solution

Language: **python3**  /  Runtime: 212 ms

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        if l1 is None: return l2
        if l2 is None: return l1
        a1 = []
        while l1 and l1.val is not None:
            a1.append(str(l1.val))
            l1 = l1.next
        a2 = []
        while l2 and l2.val is not None:
            a2.append(str(l2.val))
            l2 = l2.next
        s = list(map(int, list(str(int(''.join(a1)) + int(''.join(a2))))))
        res = p = ListNode(None)
        for si in s:
            p.next = ListNode(si)
            p = p.next
        return res.next
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-two-numbers-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-two-numbers-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-two-numbers-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-two-numbers-ii/)