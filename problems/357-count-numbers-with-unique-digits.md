# 357. Count Numbers with Unique Digits | 计算各个位数不同的数字个数

## Question description

<!--If you want to use the English description, use <p>Given a <b>non-negative</b> integer n, count all numbers with unique digits, x, where 0 &le; x &lt; 10<sup>n</sup>.</p>

<div>
<p><strong>Example:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">2</span>
<strong>Output: </strong><span id="example-output-1">91 
<strong>Explanation: </strong></span>The answer should be the total numbers in the range of 0 &le; x &lt; 100, 
&nbsp;            excluding <code>11,22,33,44,55,66,77,88,99</code>
</pre>
</div> instead-->
<p>给定一个<strong>非负</strong>整数 n，计算各位数字都不同的数字 x 的个数，其中 0 &le; x &lt; 10<sup>n&nbsp;</sup>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>91 
<strong>解释: </strong>答案应为除去 <code>11,22,33,44,55,66,77,88,99 </code>外，在 [0,100) 区间内的所有数字。
</pre>




## Solution

Language: **python3**  /  Runtime: 32 ms

```python3
class Solution:
    def countNumbersWithUniqueDigits(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0:
            return 1
        else:
            n = min(n, 10)
            arr = [9, 9, 8, 7, 6, 5, 4, 3, 2, 1]
            a = self.countNumbersWithUniqueDigits(n-1)
            b = 1
            for i in range(n):
                b *= arr[i]
            return a + b

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-numbers-with-unique-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-numbers-with-unique-digits/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-numbers-with-unique-digits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-numbers-with-unique-digits/)