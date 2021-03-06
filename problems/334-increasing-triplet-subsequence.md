# 334. Increasing Triplet Subsequence | 递增的三元子序列

## Question description

<!--If you want to use the English description, use <p>Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.</p>

<p>Formally the function should:</p>

<blockquote>Return true if there exists <i>i, j, k </i><br />
such that <i>arr[i]</i> &lt; <i>arr[j]</i> &lt; <i>arr[k]</i> given 0 &le; <i>i</i> &lt; <i>j</i> &lt; <i>k</i> &le; <i>n</i>-1 else return false.</blockquote>

<p><strong>Note: </strong>Your algorithm should run in O(<i>n</i>) time complexity and O(<i>1</i>) space complexity.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3,4,5]</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[5,4,3,2,1]</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>
</div>
</div> instead-->
<p>给定一个未排序的数组，判断这个数组中是否存在长度为 3 的递增子序列。</p>

<p>数学表达式如下:</p>

<blockquote>如果存在这样的&nbsp;<em>i, j, k,&nbsp;</em>&nbsp;且满足&nbsp;0 &le; <em>i</em> &lt; <em>j</em> &lt; <em>k</em> &le; <em>n</em>-1，<br>
使得&nbsp;<em>arr[i]</em> &lt; <em>arr[j]</em> &lt; <em>arr[k] </em>，返回 true ;&nbsp;否则返回 false 。</blockquote>

<p><strong>说明:</strong> 要求算法的时间复杂度为 O(<em>n</em>)，空间复杂度为 O(<em>1</em>) 。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>[1,2,3,4,5]
<strong>输出: </strong>true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>[5,4,3,2,1]
<strong>输出: </strong>false</pre>


## Note

基于候选的思想。


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        int c1 = INT_MAX, c2 = INT_MAX;
        for (int n : nums) {
            if (n <= c1) {
                c1 = n;
            } else if (n <= c2) {
                c2 = n;
            } else {
                return true;
            }
        }
        return false;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/increasing-triplet-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/increasing-triplet-subsequence/description/)

Solution: [LeetCode](https://leetcode.com/articles/increasing-triplet-subsequence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/increasing-triplet-subsequence/)