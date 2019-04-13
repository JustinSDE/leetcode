# 368. Largest Divisible Subset | 最大整除子集

## Question description

<!--If you want to use the English description, use <p>Given a set of <b>distinct</b> positive integers, find the largest subset such that every pair (S<sub>i</sub>, S<sub>j</sub>) of elements in this subset satisfies:</p>

<p>S<sub>i</sub> % S<sub>j</sub> = 0 or S<sub>j</sub> % S<sub>i</sub> = 0.</p>

<p>If there are multiple solutions, return any subset is fine.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3]</span>
<strong>Output: </strong><span id="example-output-1">[1,2] </span>(of course, [1,3] will also be ok)
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,4,8]</span>
<strong>Output: </strong><span id="example-output-2">[1,2,4,8]</span>
</pre>
</div>
</div> instead-->
<p>给出一个由<strong>无重复的</strong>正整数组成的集合，找出其中最大的整除子集，子集中任意一对 (S<sub>i，</sub>S<sub>j</sub>) 都要满足：S<sub>i</sub> % S<sub>j</sub> = 0 或 S<sub>j</sub> % S<sub>i</sub> = 0。</p>

<p>如果有多个目标子集，返回其中任何一个均可。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
<strong>输出:</strong> [1,2] (当然, [1,3] 也正确)
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [1,2,4,8]
<strong>输出:</strong> [1,2,4,8]
</pre>




## Solution

Language: **cpp**  /  Runtime: 28 ms

```cpp
class Solution {
public:
    vector<int> largestDivisibleSubset(vector<int>& nums) {
        vector<int> res;
        sort(nums.begin(), nums.end());
        int size = nums.size();
        // corner case
        if (size == 0) {
            return res;
        }
        // longest subset's length endswith current element
        vector<int> dp(size, 1);
        // for the subset endswith current element, the index of previous element
        // we can get solution subset from this list
        vector<int> path(size, -1);
        // last element's index of current longest subset
        int ans = 0;
        for (int i = 0; i < size; ++i) {
            for (int j = 0; j < i; ++j) {
                if (nums[i] % nums[j] == 0 && dp[i] < dp[j] + 1) {
                    dp[i] = dp[j] + 1;
                    path[i] = j;
                }
            }
            if (dp[i] > dp[ans]) {
                ans = i;
            }
        }

        // get solution subset 
        for (int i = ans; i != -1; i = path[i]) {
            res.push_back(nums[i]);
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-divisible-subset/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-divisible-subset/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-divisible-subset/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-divisible-subset/)