# 367. Valid Perfect Square | 有效的完全平方数

## Question description

<!--If you want to use the English description, use <p>Given a positive integer <i>num</i>, write a function which returns True if <i>num</i> is a perfect square else False.</p>

<p><b>Note:</b> <b>Do not</b> use any built-in library function such as <code>sqrt</code>.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">16</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">14</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>
</div>
</div> instead-->
<p>给定一个正整数 <em>num</em>，编写一个函数，如果 <em>num</em> 是一个完全平方数，则返回 True，否则返回 False。</p>

<p><strong>说明：</strong>不要使用任何内置的库函数，如&nbsp; <code>sqrt</code>。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>16
<strong>输出：</strong>True</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>14
<strong>输出：</strong>False
</pre>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def isPerfectSquare(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num % 10 in (2, 3, 7, 8):
            return False
        i = 1
        while num > 0:
            num -= i
            if num == 0:
                return True
            i += 2
        return False
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/valid-perfect-square/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-perfect-square/description/)

Solution: [LeetCode](https://leetcode.com/articles/valid-perfect-square/)  /  [LeetCode中国](https://leetcode-cn.com/articles/valid-perfect-square/)