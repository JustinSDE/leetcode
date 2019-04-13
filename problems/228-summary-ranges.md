# 228. Summary Ranges | 汇总区间

## Question description

<!--If you want to use the English description, use <p>Given a sorted integer array without duplicates, return the summary of its ranges.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b>  [0,1,2,4,5,7]
<b>Output:</b> [&quot;0-&gt;2&quot;,&quot;4-&gt;5&quot;,&quot;7&quot;]
<strong>Explanation: </strong>0,1,2 form a continuous range;&nbsp;4,5 form a continuous range.
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b>  [0,2,3,4,6,8,9]
<b>Output:</b> [&quot;0&quot;,&quot;2-&gt;4&quot;,&quot;6&quot;,&quot;8-&gt;9&quot;]
<strong>Explanation: </strong>2,3,4 form a continuous range;&nbsp;8,9 form a continuous range.
</pre>
 instead-->
<p>给定一个无重复元素的有序整数数组，返回数组区间范围的汇总。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [0,1,2,4,5,7]
<strong>输出:</strong> [&quot;0-&gt;2&quot;,&quot;4-&gt;5&quot;,&quot;7&quot;]
<strong>解释: </strong>0,1,2 可组成一个连续的区间;&nbsp;4,5 可组成一个连续的区间。</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [0,2,3,4,6,8,9]
<strong>输出:</strong> [&quot;0&quot;,&quot;2-&gt;4&quot;,&quot;6&quot;,&quot;8-&gt;9&quot;]
<strong>解释: </strong>2,3,4 可组成一个连续的区间;&nbsp;8,9 可组成一个连续的区间。</pre>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> res;
        if (nums.empty()) return res;
        int i = 0;
        while (i < nums.size()) {
            int st = nums[i];
            int ed = st;
            while (i < nums.size() - 1 && nums[i+1] - nums[i] == 1) {
                ed = nums[i+1];
                i++;
            }
            if (st == ed) {
                res.push_back(to_string(st));
            } else {
                string s = to_string(st) + "->" + to_string(ed);
                res.push_back(s);
            }
            i++;
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/summary-ranges/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/summary-ranges/description/)

Solution: [LeetCode](https://leetcode.com/articles/summary-ranges/)  /  [LeetCode中国](https://leetcode-cn.com/articles/summary-ranges/)