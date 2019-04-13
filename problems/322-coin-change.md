# 322. Coin Change | 零钱兑换

## Question description

<!--If you want to use the English description, use <p>You are given coins of different denominations and a total amount of money <i>amount</i>. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return <code>-1</code>.</p>

<p><b>Example 1:</b></p>

<pre>
<strong>Input: </strong>coins = <code>[1, 2, 5]</code>, amount = <code>11</code>
<strong>Output: </strong><code>3</code> 
<strong>Explanation:</strong> 11 = 5 + 5 + 1</pre>

<p><b>Example 2:</b></p>

<pre>
<strong>Input: </strong>coins = <code>[2]</code>, amount = <code>3</code>
<strong>Output: </strong>-1
</pre>

<p><b>Note</b>:<br />
You may assume that you have an infinite number of each kind of coin.</p>
 instead-->
<p>给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回&nbsp;<code>-1</code>。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>coins = <code>[1, 2, 5]</code>, amount = <code>11</code>
<strong>输出: </strong><code>3</code> 
<strong>解释:</strong> 11 = 5 + 5 + 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>coins = <code>[2]</code>, amount = <code>3</code>
<strong>输出: </strong>-1</pre>

<p><strong>说明</strong>:<br>
你可以认为每种硬币的数量是无限的。</p>


## Note

1、动态规划

初始状态：`dp[i] = INT_MAX, dp[0] = 0`

状态转移：”` dp[i] = min(dp[i], dp[i - coin] + 1)`

注意int溢出。



2、搜索+剪枝

使用搜索算法，尽量使用大额硬币。注意剪枝：如果是最小面额，检查能否整除剩余金额；每次递归前，只有比当前最优解更好才进行递归，否则跳出（剪枝，这步剪枝很关键）。


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
// refer: https://www.bilibili.com/video/av31621107
class Solution {
public:
    void backTacking(vector<int>& coins, int amount, int index, int cur, int& res) {
        int coin = coins[index];
        if (index == 0) {
            if (amount % coin == 0) {
                res = min(res, cur + amount / coin);
            }
        } else {
            for (int n = amount / coin; n >= 0 && cur + n < res; --n) {
                backTacking(coins, amount - n * coin, index - 1, cur + n, res);
            }
        }
    }

    int coinChange(vector<int>& coins, int amount) {
        sort(coins.begin(), coins.end());
        int res = INT_MAX;
        backTacking(coins, amount, coins.size() - 1, 0, res);
        return res == INT_MAX ? -1 : res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/coin-change/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/coin-change/description/)

Solution: [LeetCode](https://leetcode.com/articles/coin-change/)  /  [LeetCode中国](https://leetcode-cn.com/articles/coin-change/)