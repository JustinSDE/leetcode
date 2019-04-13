# 2. Add Two Numbers | 两数相加

## Question description

<!--If you want to use the English description, use <p>You are given two <b>non-empty</b> linked lists representing two non-negative integers. The digits are stored in <b>reverse order</b> and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> (2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<b>Output:</b> 7 -&gt; 0 -&gt; 8
<b>Explanation:</b> 342 + 465 = 807.
</pre>
 instead-->
<p>给出两个&nbsp;<strong>非空</strong> 的链表用来表示两个非负的整数。其中，它们各自的位数是按照&nbsp;<strong>逆序</strong>&nbsp;的方式存储的，并且它们的每个节点只能存储&nbsp;<strong>一位</strong>&nbsp;数字。</p>

<p>如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。</p>

<p>您可以假设除了数字 0 之外，这两个数都不会以 0&nbsp;开头。</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>(2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<strong>输出：</strong>7 -&gt; 0 -&gt; 8
<strong>原因：</strong>342 + 465 = 807
</pre>


## Note

实际上就是考查大数相加，以链表的形式。不过，有几点需要注意：

1、空链表判断

2、链表可能长度不一致

3、可能会有进位，进位需要传递到下一节点，节点值=节点和+进位。

4、尾部不要添加多余的节点


## Solution

Language: **java**  /  Runtime: 20 ms

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(-1);
        ListNode t = dummy;
        int carry = 0;
        while (carry > 0 || l1 != null || l2 != null) {
            int sum = carry + (l1 == null ? 0 : l1.val) + (l2 == null ? 0 : l2.val);
            t.next = new ListNode(sum % 10);
            carry = sum / 10;
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
            t = t.next;
        }
        return dummy.next;
    }
}
```

Language: **cpp**  /  Runtime: 28 ms

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        if(!l1){
            return l2;
        }
        if(!l2){
            return l1;
        }
        ListNode* rst = new ListNode(NULL);
        int n1, n2;
        ListNode* res = rst;
        while(true){
            if(l1){
                n1 = l1->val;
                l1 = l1->next;
            }else{
                n1 = NULL;
            }
            if(l2){
                n2 = l2->val;
                l2 = l2->next;
            }else{
                n2 = NULL;
            }
            rst->val += (int)n1 + (int)n2;
            if(l1 || l2 || rst->val >= 10){
                rst->next = new ListNode(rst->val / 10);
                rst->val %= 10;
                rst = rst->next;
            }else{
                break;
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-two-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-two-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-two-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-two-numbers/)