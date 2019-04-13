# 138. Copy List with Random Pointer | 复制带随机指针的链表

## Question description

<!--If you want to use the English description, use <p>A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null.</p>

<p>Return a <a href="https://en.wikipedia.org/wiki/Object_copying#Deep_copy" target="_blank"><strong>deep copy</strong></a> of the list.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://discuss.leetcode.com/uploads/files/1470150906153-2yxeznm.png" style="width: 375px; height: 129px;" /></strong></p>

<pre>
<strong>Input:
</strong><span id="example-input-1-1">{&quot;$id&quot;:&quot;1&quot;,&quot;next&quot;:{&quot;$id&quot;:&quot;2&quot;,&quot;next&quot;:null,&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:2},&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:1}
</span>
<b>Explanation:
</b>Node 1&#39;s value is 1, both of its next and random pointer points to Node 2.
Node 2&#39;s value is 2, its next pointer points to null and its random pointer points to itself.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>You must return the <strong>copy of the given head</strong>&nbsp;as a reference to the cloned list.</li>
</ol> instead-->
<p>给定一个链表，每个节点包含一个额外增加的随机指针，该指针可以指向链表中的任何节点或空节点。</p>

<p>要求返回这个链表的<strong><a href="https://baike.baidu.com/item/深拷贝/22785317?fr=aladdin" target="_blank">深拷贝</a></strong>。&nbsp;</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/1470150906153-2yxeznm.png"></strong></p>

<pre><strong>输入：
</strong>{&quot;$id&quot;:&quot;1&quot;,&quot;next&quot;:{&quot;$id&quot;:&quot;2&quot;,&quot;next&quot;:null,&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:2},&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:1}

<strong>解释：
</strong>节点 1 的值是 1，它的下一个指针和随机指针都指向节点 2 。
节点 2 的值是 2，它的下一个指针指向 null，随机指针指向它自己。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>你必须返回<strong>给定头的拷贝</strong>作为对克隆列表的引用。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 48 ms

```cpp
/**
 * Definition for singly-linked list with a random pointer.
 * struct RandomListNode {
 *     int label;
 *     RandomListNode *next, *random;
 *     RandomListNode(int x) : label(x), next(NULL), random(NULL) {}
 * };
 */
class Solution {
public:
    unordered_map<RandomListNode*, RandomListNode*> M;
    RandomListNode *copyRandomList(RandomListNode *head) {
        if (!head) return NULL;
        if (M.count(head)) return M[head];
        RandomListNode* tmp = new RandomListNode(head->label);
        M.insert({head, tmp});
        if (head->next) tmp->next = copyRandomList(head->next);
        if (head->random) tmp->random = copyRandomList(head->random);
        return tmp;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/copy-list-with-random-pointer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/copy-list-with-random-pointer/description/)

Solution: [LeetCode](https://leetcode.com/articles/copy-list-with-random-pointer/)  /  [LeetCode中国](https://leetcode-cn.com/articles/copy-list-with-random-pointer/)