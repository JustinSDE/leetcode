# 643. Maximum Average Subarray I | 子数组最大平均数 I

## Question description

<!--If you want to use the English description, use <p>Given an array consisting of <code>n</code> integers, find the contiguous subarray of given length <code>k</code> that has the maximum average value. And you need to output the maximum average value.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [1,12,-5,-6,50,3], k = 4
<b>Output:</b> 12.75
<b>Explanation:</b> Maximum average is (12-5-6+50)/4 = 51/4 = 12.75
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>1 &lt;= <code>k</code> &lt;= <code>n</code> &lt;= 30,000.</li>
	<li>Elements of the given array will be in the range [-10,000, 10,000].</li>
</ol>

<p>&nbsp;</p>
 instead-->
<p>给定 <code>n</code> 个整数，找出平均数最大且长度为 <code>k</code> 的连续子数组，并输出该最大平均数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,12,-5,-6,50,3], k = 4
<strong>输出:</strong> 12.75
<strong>解释:</strong> 最大平均数 (12-5-6+50)/4 = 51/4 = 12.75
</pre>

<p>&nbsp;</p>

<p><strong>注意:</strong></p>

<ol>
	<li>1 &lt;= <code>k</code> &lt;= <code>n</code> &lt;= 30,000。</li>
	<li>所给数据范围 [-10,000，10,000]。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 188 ms

```python3
class Solution:
    def findMaxAverage(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: float
        """
        dp = [sum(nums[:k])]
        for i in range(1, len(nums) - k + 1):
            dp.append(dp[i-1] - nums[i-1] + nums[i+k-1])
        return max(dp) / k
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-average-subarray-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-average-subarray-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-average-subarray-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-average-subarray-i/)