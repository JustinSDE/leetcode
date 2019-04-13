# 279. Perfect Squares | 完全平方数

## Question description

<!--If you want to use the English description, use <p>Given a positive integer <i>n</i>, find the least number of perfect square numbers (for example, <code>1, 4, 9, 16, ...</code>) which sum to <i>n</i>.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> <i>n</i> = <code>12</code>
<b>Output:</b> 3 
<strong>Explanation: </strong><code>12 = 4 + 4 + 4.</code></pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> <i>n</i> = <code>13</code>
<b>Output:</b> 2
<strong>Explanation: </strong><code>13 = 4 + 9.</code></pre> instead-->
<p>给定正整数&nbsp;<em>n</em>，找到若干个完全平方数（比如&nbsp;<code>1, 4, 9, 16, ...</code>）使得它们的和等于<em> n</em>。你需要让组成和的完全平方数的个数最少。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> <em>n</em> = <code>12</code>
<strong>输出:</strong> 3 
<strong>解释: </strong><code>12 = 4 + 4 + 4.</code></pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <em>n</em> = <code>13</code>
<strong>输出:</strong> 2
<strong>解释: </strong><code>13 = 4 + 9.</code></pre>




## Solution

Language: **cpp**  /  Runtime: 96 ms

```cpp
class Solution {
public:
    int numSquares(int n) {
        vector<int> dp(n + 1, INT_MAX);
        dp[0] = 0;
        for (int i = 1; i <= n; ++i) {
            for (int j = (int)sqrt(i); j >= 1; --j) {
                dp[i] = min(dp[i], 1 + dp[i - j * j]);
            }
        }
        return dp[n];
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/perfect-squares/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/perfect-squares/description/)

Solution: [LeetCode](https://leetcode.com/articles/perfect-squares/)  /  [LeetCode中国](https://leetcode-cn.com/articles/perfect-squares/)