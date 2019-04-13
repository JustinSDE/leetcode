# 53. Maximum Subarray | 最大子序和

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, find the contiguous subarray&nbsp;(containing at least one number) which has the largest sum and return its sum.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [-2,1,-3,4,-1,2,1,-5,4],
<strong>Output:</strong> 6
<strong>Explanation:</strong>&nbsp;[4,-1,2,1] has the largest sum = 6.
</pre>

<p><strong>Follow up:</strong></p>

<p>If you have figured out the O(<em>n</em>) solution, try coding another solution using the divide and conquer approach, which is more subtle.</p>
 instead-->
<p>给定一个整数数组 <code>nums</code>&nbsp;，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [-2,1,-3,4,-1,2,1,-5,4],
<strong>输出:</strong> 6
<strong>解释:</strong>&nbsp;连续子数组&nbsp;[4,-1,2,1] 的和最大，为&nbsp;6。
</pre>

<p><strong>进阶:</strong></p>

<p>如果你已经实现复杂度为 O(<em>n</em>) 的解法，尝试使用更为精妙的分治法求解。</p>


## Note

这题Wrong Answer了很多次。

先求数组的累加和，然后在累加和数组最前面插个0。然后，问题就转化成了类似[Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)。为什么说类似呢？因为，买卖股票的问题可以不发生交易，但本题，子数组不能为空。所以，当不发生交易时，就返回数组的最大值。


## Solution

Language: **python3**  /  Runtime: 52 ms

```python3
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 0:
            return 
        prices = list(itertools.accumulate(nums))
        prices.insert(0, 0)
        min_price = prices[0]
        dp = [0] * len(prices)
        for i in range(1, len(prices)):
            dp[i] = max(dp[i-1], prices[i] - min_price)
            min_price = min(min_price, prices[i])
        if dp[-1] == 0:
            return max(nums)
        else:
            return dp[-1]
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-subarray/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-subarray/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-subarray/)