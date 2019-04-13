# 152. Maximum Product Subarray | 乘积最大子序列

## Question description

<!--If you want to use the English description, use <p>Given an integer array&nbsp;<code>nums</code>, find the contiguous subarray within an array (containing at least one number) which has the largest product.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,-2,4]
<strong>Output:</strong> <code>6</code>
<strong>Explanation:</strong>&nbsp;[2,3] has the largest product 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [-2,0,-1]
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;The result cannot be 2, because [-2,-1] is not a subarray.</pre>
 instead-->
<p>给定一个整数数组 <code>nums</code>&nbsp;，找出一个序列中乘积最大的连续子序列（该序列至少包含一个数）。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [2,3,-2,4]
<strong>输出:</strong> <code>6</code>
<strong>解释:</strong>&nbsp;子数组 [2,3] 有最大乘积 6。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [-2,0,-1]
<strong>输出:</strong> 0
<strong>解释:</strong>&nbsp;结果不能为 2, 因为 [-2,-1] 不是子数组。</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        if (nums.size() == 0) return 0;
        vector<int> dp(nums.size(), 0);
        dp[0] = nums[0];
        int pre = nums[0] < 0 ? 0 : -1;
        for (int i=1; i<nums.size(); ++i) {
            if (nums[i] >= 0) {
                dp[i] = max(nums[i], nums[i] * dp[i-1]);
            } else {
                if (pre != -1) {
                    int k = 1;
                    for (int j=pre; j<=i; ++j) {
                        k *= nums[j];
                    }
                    dp[i] = max(k, k * dp[pre-1]);
                }
                pre = i;
            }
        }
        return *max_element(dp.begin(), dp.end());
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-subarray/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-subarray/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-subarray/)