# 221. Maximal Square | 最大正方形

## Question description

<!--If you want to use the English description, use <p>Given a 2D binary matrix filled with 0&#39;s and 1&#39;s, find the largest square containing only 1&#39;s and return its area.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input: 
</strong>
1 0 1 0 0
1 0 <font color="red">1</font> <font color="red">1</font> 1
1 1 <font color="red">1</font> <font color="red">1</font> 1
1 0 0 1 0

<strong>Output: </strong>4
</pre> instead-->
<p>在一个由 0 和 1 组成的二维矩阵内，找到只包含 1 的最大正方形，并返回其面积。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入: 
</strong>
1 0 1 0 0
1 0 <strong>1 1</strong> 1
1 1 <strong>1 1 </strong>1
1 0 0 1 0

<strong>输出: </strong>4</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        /* F[i][j]   The maximum square length when the current position is the lower right corner
        up: F[i-1][j]   left: F[i][j-1]
        matrix[i][j] == '1':
        if up != left   F[i][j] = min(up, left) + 1
        if up == left   F[i][j] = up + matrix[i-up][j-up] == '1'
        matrix[i][j] != '1':  0
        Use scrolling array optimization
        */
        if (!matrix.size() || !matrix[0].size()) return 0;
        int n = matrix.size();
        int m = matrix[0].size();
        vector<int> dp(m+1, 0);
        int res = 0;
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                if (matrix[i][j] == '1') {
                    if (dp[j+1] != dp[j]) {
                        dp[j+1] = min(dp[j+1], dp[j]) + 1;
                    } else {
                        dp[j+1] += matrix[i-dp[j]][j-dp[j]] == '1';
                    }
                } else {
                    dp[j+1] = 0;
                }
                // collect max length
                res = max(res, dp[j+1]);
                // cout << dp[j+1] << " ";
            }
            // cout << endl;
        }
        return res * res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximal-square/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximal-square/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximal-square/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximal-square/)