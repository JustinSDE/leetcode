# 268. Missing Number | 缺失数字

## Question description

<!--If you want to use the English description, use <p>Given an array containing <i>n</i> distinct numbers taken from <code>0, 1, 2, ..., n</code>, find the one that is missing from the array.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [3,0,1]
<b>Output:</b> 2
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [9,6,4,2,3,5,7,0,1]
<b>Output:</b> 8
</pre>

<p><b>Note</b>:<br />
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?</p> instead-->
<p>给定一个包含 <code>0, 1, 2, ..., n</code>&nbsp;中&nbsp;<em>n</em>&nbsp;个数的序列，找出 0 .. <em>n</em>&nbsp;中没有出现在序列中的那个数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [3,0,1]
<strong>输出:</strong> 2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [9,6,4,2,3,5,7,0,1]
<strong>输出:</strong> 8
</pre>

<p><strong>说明:</strong><br>
你的算法应具有线性时间复杂度。你能否仅使用额外常数空间来实现?</p>




## Solution

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        tmp = [-1] * (len(nums) + 1)
        for n in nums:
            tmp[n] = 1
        return tmp.index(-1)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/missing-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/missing-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/missing-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/missing-number/)