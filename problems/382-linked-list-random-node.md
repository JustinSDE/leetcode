# 382. Linked List Random Node | 链表随机节点

## Question description

<!--If you want to use the English description, use <p>Given a singly linked list, return a random node's value from the linked list. Each node must have the <b>same probability</b> of being chosen.</p>

<p><b>Follow up:</b><br />
What if the linked list is extremely large and its length is unknown to you? Could you solve this efficiently without using extra space?
</p>

<p><b>Example:</b>
<pre>
// Init a singly linked list [1,2,3].
ListNode head = new ListNode(1);
head.next = new ListNode(2);
head.next.next = new ListNode(3);
Solution solution = new Solution(head);

// getRandom() should return either 1, 2, or 3 randomly. Each element should have equal probability of returning.
solution.getRandom();
</pre>
</p> instead-->
<p>给定一个单链表，随机选择链表的一个节点，并返回相应的节点值。保证每个节点<strong>被选的概率一样</strong>。</p>

<p><strong>进阶:</strong><br />
如果链表十分大且长度未知，如何解决这个问题？你能否使用常数级空间复杂度实现？</p>

<p><strong>示例:</strong></p>

<pre>
// 初始化一个单链表 [1,2,3].
ListNode head = new ListNode(1);
head.next = new ListNode(2);
head.next.next = new ListNode(3);
Solution solution = new Solution(head);

// getRandom()方法应随机返回1,2,3中的一个，保证每个元素被返回的概率相等。
solution.getRandom();
</pre>


## Note

蓄水池抽样算法。

参考文章：[数据工程师必知算法：蓄水池抽样 - 文章 - 伯乐在线](http://blog.jobbole.com/42550/)


## Solution

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
    /** @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node. */
    ListNode* H;
    Solution(ListNode* head) {
        H = head;
    }
    
    /** Returns a random node's value. */
    int getRandom() {
        int n = 1;
        ListNode* p = H;
        int res = p->val;
        while (p->next) {
            p = p->next;
            n++;
            if (rand() % n == 0) {
                res = p->val;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(head);
 * int param_1 = obj.getRandom();
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/linked-list-random-node/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/linked-list-random-node/description/)

Solution: [LeetCode](https://leetcode.com/articles/linked-list-random-node/)  /  [LeetCode中国](https://leetcode-cn.com/articles/linked-list-random-node/)