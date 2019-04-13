# 633. Sum of Square Numbers | 平方数之和

## Question description

<!--If you want to use the English description, use <p>Given a non-negative integer <code>c</code>, your task is to decide whether there&#39;re two integers <code>a</code> and <code>b</code> such that a<sup>2</sup> + b<sup>2</sup> = c.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> 5
<b>Output:</b> True
<b>Explanation:</b> 1 * 1 + 2 * 2 = 5
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> 3
<b>Output:</b> False
</pre>

<p>&nbsp;</p>
 instead-->
<p>给定一个非负整数&nbsp;<code>c</code>&nbsp;，你要判断是否存在两个整数 <code>a</code> 和 <code>b</code>，使得&nbsp;a<sup>2</sup> + b<sup>2</sup> = c。</p>

<p><strong>示例1:</strong></p>

<pre>
<strong>输入:</strong> 5
<strong>输出:</strong> True
<strong>解释:</strong> 1 * 1 + 2 * 2 = 5
</pre>

<p>&nbsp;</p>

<p><strong>示例2:</strong></p>

<pre>
<strong>输入:</strong> 3
<strong>输出:</strong> False
</pre>




## Solution

Language: **python3**  /  Runtime: 212 ms

```python3
class Solution:
    def judgeSquareSum(self, c):
        """
        :type c: int
        :rtype: bool
        """
        tmp = set()
        for i in range(int(c**0.5)+1):
            tmp.add(i*i)
        for ii in tmp:
            if c - ii in tmp:
                return True
        return False
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-square-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-square-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-square-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-square-numbers/)