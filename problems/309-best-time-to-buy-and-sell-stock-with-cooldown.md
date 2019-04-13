# 309. Best Time to Buy and Sell Stock with Cooldown | 最佳买卖股票时机含冷冻期

## Question description

<!--If you want to use the English description, use <p>Say you have an array for which the <i>i</i><sup>th</sup> element is the price of a given stock on day <i>i</i>.</p>

<p>Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:</p>

<ul>
	<li>You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).</li>
	<li>After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)</li>
</ul>

<p><b>Example:</b></p>

<pre>
<strong>Input:</strong> [1,2,3,0,2]
<strong>Output: </strong>3 
<strong>Explanation:</strong> transactions = [buy, sell, cooldown, buy, sell]
</pre> instead-->
<p>给定一个整数数组，其中第<em>&nbsp;i</em>&nbsp;个元素代表了第&nbsp;<em>i</em>&nbsp;天的股票价格 。​</p>

<p>设计一个算法计算出最大利润。在满足以下约束条件下，你可以尽可能地完成更多的交易（多次买卖一支股票）:</p>

<ul>
	<li>你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</li>
	<li>卖出股票后，你无法在第二天买入股票 (即冷冻期为 1 天)。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,3,0,2]
<strong>输出: </strong>3 
<strong>解释:</strong> 对应的交易状态为: [买入, 卖出, 冷冻期, 买入, 卖出]</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
// refer: https://www.bilibili.com/video/av31578180
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        /*
              hold -> sell      hold -> hold      check ways into hold: hold[i] = max(hold[i-1], rest[i-1] - prices[i])
              sell -> rest                        check ways into sell: sell[i] = hold[i-1] + prices[i]
              rest -> hold      rest -> rest      check ways into rest: rest[i] = max(rest[i-1], sell[i-1])
        */
        int hold = INT_MIN;
        int sell = 0;
        int rest = 0;
        for (int price : prices) {
            int tmp = rest;  // rest[i-1]
            rest = max(rest, sell);  // rest[i]
            sell = hold + price;  // sell[i]
            hold = max(hold, tmp - price);  // hold[i]
        }
        return max(sell, rest);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)

Solution: [LeetCode](https://leetcode.com/articles/best-time-to-buy-and-sell-stock-with-cooldown/)  /  [LeetCode中国](https://leetcode-cn.com/articles/best-time-to-buy-and-sell-stock-with-cooldown/)