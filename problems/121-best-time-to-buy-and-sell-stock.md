# 121. Best Time to Buy and Sell Stock | 买卖股票的最佳时机

## Question description

<!--If you want to use the English description, use <p>Say you have an array for which the <em>i</em><sup>th</sup> element is the price of a given stock on day <em>i</em>.</p>

<p>If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.</p>

<p>Note that you cannot sell a stock before you buy one.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [7,1,5,3,6,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
&nbsp;            Not 7-1 = 6, as selling price needs to be larger than buying price.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transaction is done, i.e. max profit = 0.
</pre>
 instead-->
<p>给定一个数组，它的第&nbsp;<em>i</em> 个元素是一支给定股票第 <em>i</em> 天的价格。</p>

<p>如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。</p>

<p>注意你不能在买入股票前卖出股票。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [7,1,5,3,6,4]
<strong>输出:</strong> 5
<strong>解释: </strong>在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [7,6,4,3,1]
<strong>输出:</strong> 0
<strong>解释: </strong>在这种情况下, 没有交易完成, 所以最大利润为 0。
</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int res = 0;
        int buy = INT_MAX;
        for (int p : prices) {
            buy = min(buy, p);
            res = max(res, p - buy);
        }
        return res;
    }
};
```

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int maxProfit(int[] prices) {
        int res = 0, buy = Integer.MAX_VALUE;
        for (int p : prices) {
            buy = Math.min(buy , p);
            res = Math.max(res, p - buy);
        }
        return res;
    }
}
```

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def maxProfit(self, prices):
        if(len(prices) < 2):
            return 0
        max_profit, min_price = 0, prices[0]
        for i in range(1, len(prices)):
            if prices[i] > prices[i-1]:
                max_profit = max(max_profit, prices[i] - min_price)
            else:
                min_price = min(min_price, prices[i])
        return max_profit
```

Language: **c**  /  Runtime: 642 ms

```c
int maxProfit(int* prices, int pricesSize) {
    int max = 0, tmp = 0;
    for(int i = 0; i < pricesSize-1; i++){
        for(int j = i+1; j < pricesSize; j++){
            tmp = *(prices+j) - *(prices+i);
            if(tmp > max)
                max = tmp;
        }
    }
    return max;
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/description/)

Solution: [LeetCode](https://leetcode.com/articles/best-time-to-buy-and-sell-stock/)  /  [LeetCode中国](https://leetcode-cn.com/articles/best-time-to-buy-and-sell-stock/)