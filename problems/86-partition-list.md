# 86. Partition List | 分隔链表

## Question description

<!--If you want to use the English description, use <p>Given a linked list and a value <em>x</em>, partition it such that all nodes less than <em>x</em> come before nodes greater than or equal to <em>x</em>.</p>

<p>You should preserve the original relative order of the nodes in each of the two partitions.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> head = 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;2, <em>x</em> = 3
<strong>Output:</strong> 1-&gt;2-&gt;2-&gt;4-&gt;3-&gt;5
</pre>
 instead-->
<p>给定一个链表和一个特定值<em> x</em>，对链表进行分隔，使得所有小于 <em>x</em> 的节点都在大于或等于 <em>x</em> 的节点之前。</p>

<p>你应当保留两个分区中每个节点的初始相对位置。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> head = 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;2, <em>x</em> = 3
<strong>输出:</strong> 1-&gt;2-&gt;2-&gt;4-&gt;3-&gt;5
</pre>


## Note

正常来讲，应该通过调整链表的指针来实现，要考虑的细节比较多。一种比较取巧的方式是：遍历得到数组，然后排序，然后修改链表节点的值。


## Solution

Language: **python3**  /  Runtime: 68 ms

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def partition(self, head, x):
        """
        :type head: ListNode
        :type x: int
        :rtype: ListNode
        """
        if head is None:
            return head
        it = head
        arr = []
        while it is not None:
            arr.append(it.val)
            it = it.next
        arr.sort(key=lambda _: _ >= x)
        it = head
        i = 0
        while it is not None:
            it.val = arr[i]
            it = it.next
            i += 1
        return head
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/partition-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/partition-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/partition-list/)