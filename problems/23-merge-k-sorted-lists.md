# 23. Merge k Sorted Lists | 合并K个排序链表

## Question description

<!--If you want to use the English description, use <p>Merge <em>k</em> sorted linked lists and return it as one sorted list. Analyze and describe its complexity.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
[
&nbsp; 1-&gt;4-&gt;5,
&nbsp; 1-&gt;3-&gt;4,
&nbsp; 2-&gt;6
]
<strong>Output:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>
 instead-->
<p>合并&nbsp;<em>k&nbsp;</em>个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
&nbsp; 1-&gt;4-&gt;5,
&nbsp; 1-&gt;3-&gt;4,
&nbsp; 2-&gt;6
]
<strong>输出:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6</pre>




## Solution

Language: **cpp**  /  Runtime: 24 ms

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto x = [](){
    ios::sync_with_stdio(false);
    cin.tie(NULL);
    return 0;
}();
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        auto cmp = [](int x, int y) { return x > y; };
        priority_queue<int, vector<int>, decltype(cmp)> pq(cmp);
        for (auto t : lists) {
            while (t) {
                pq.push(t->val);
                t = t->next;
            }
        }
        ListNode* p = new ListNode(-1);
        ListNode* res = p;
        while (!pq.empty()) {
            p->next = new ListNode(pq.top());
            pq.pop();
            p = p->next;
        }
        return res->next;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-k-sorted-lists/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-k-sorted-lists/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-k-sorted-lists/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-k-sorted-lists/)