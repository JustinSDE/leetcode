# 373. Find K Pairs with Smallest Sums | 查找和最小的K对数字

## Question description

<!--If you want to use the English description, use <p>You are given two integer arrays <b>nums1</b> and <b>nums2</b> sorted in ascending order and an integer <b>k</b>.</p>

<p>Define a pair <b>(u,v)</b> which consists of one element from the first array and one element from the second array.</p>

<p>Find the k pairs <b>(u<sub>1</sub>,v<sub>1</sub>),(u<sub>2</sub>,v<sub>2</sub>) ...(u<sub>k</sub>,v<sub>k</sub>)</b> with the smallest sums.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-1-1">[1,7,11]</span>, nums2 = <span id="example-input-1-2">[2,4,6]</span>, k = <span id="example-input-1-3">3</span>
<strong>Output: </strong><span id="example-output-1">[[1,2],[1,4],[1,6]] 
<strong>Explanation: </strong></span>The first 3 pairs are returned from the sequence: 
&nbsp;            [1,2],[1,4],[1,6],[7,2],[7,4],[11,2],[7,6],[11,4],[11,6]</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums1 = [1,1,2], nums2 = [1,2,3], k = 2
<strong>Output: </strong>[1,1],[1,1]<span>
<strong>Explanation: </strong></span>The first 2 pairs are returned from the sequence: 
&nbsp;            [1,1],[1,1],[1,2],[2,1],[1,2],[2,2],[1,3],[1,3],[2,3]</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>nums1 = [1,2], nums2 = [3], k = 3
<strong>Output: </strong>[1,3],[2,3]<span>
<strong>Explanation: </strong></span>All possible pairs are returned from the sequence: [1,3],[2,3]
</pre>
 instead-->
<p>给定两个以升序排列的整形数组 <strong>nums1</strong> 和 <strong>nums2</strong>, 以及一个整数 <strong>k</strong>。</p>

<p>定义一对值&nbsp;<strong>(u,v)</strong>，其中第一个元素来自&nbsp;<strong>nums1</strong>，第二个元素来自 <strong>nums2</strong>。</p>

<p>找到和最小的 k 对数字&nbsp;<strong>(u<sub>1</sub>,v<sub>1</sub>), (u<sub>2</sub>,v<sub>2</sub>) ... (u<sub>k</sub>,v<sub>k</sub>)</strong>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> nums1 = [1,7,11], nums2 = [2,4,6], k = 3
<strong>输出:</strong> [1,2],[1,4],[1,6]
<strong>解释: </strong>返回序列中的前 3 对数：
     [1,2],[1,4],[1,6],[7,2],[7,4],[11,2],[7,6],[11,4],[11,6]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>nums1 = [1,1,2], nums2 = [1,2,3], k = 2
<strong>输出: </strong>[1,1],[1,1]
<strong>解释: </strong>返回序列中的前 2 对数：
&nbsp;    [1,1],[1,1],[1,2],[2,1],[1,2],[2,2],[1,3],[1,3],[2,3]
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入: </strong>nums1 = [1,2], nums2 = [3], k = 3 
<strong>输出:</strong> [1,3],[2,3]
<strong>解释: </strong>也可能序列中所有的数对都被返回:[1,3],[2,3]
</pre>




## Solution

Language: **cpp**  /  Runtime: 12 ms

```cpp
class Solution {
public:
    vector<pair<int, int>> kSmallestPairs(vector<int>& nums1, vector<int>& nums2, int k) {
        vector<pair<int, int> > res;
        auto cmp = [](pair<int, int>& p1, pair<int, int>& p2) {
            return p1.first + p1.second < p2.first + p2.second;
        };
        priority_queue<pair<int, int>, vector<pair<int, int> >, decltype(cmp)>pq(cmp);
        for (int n1 : nums1) {
            for (int n2 : nums2) {
                if (pq.size() < k) {
                    pq.push(make_pair(n1, n2));
                } else if (n1 + n2 < pq.top().first + pq.top().second) {
                    pq.pop();
                    pq.push(make_pair(n1, n2));
                }
                
            }
        }
        for (int i = 0; i < k && !pq.empty(); ++i) {
            res.push_back(pq.top());
            pq.pop();
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-k-pairs-with-smallest-sums/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-k-pairs-with-smallest-sums/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-k-pairs-with-smallest-sums/)