# 400. Nth Digit | 第N个数字

## Question description

<!--If you want to use the English description, use <p>Find the <i>n</i><sup>th</sup> digit of the infinite integer sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... </p>

<p><b>Note:</b><br />
<i>n</i> is positive and will fit within the range of a 32-bit signed integer (<i>n</i> < 2<sup>31</sup>).
</p>

<p><b>Example 1:</b>
<pre>
<b>Input:</b>
3

<b>Output:</b>
3
</pre>
</p>

<p><b>Example 2:</b>
<pre>
<b>Input:</b>
11

<b>Output:</b>
0

<b>Explanation:</b>
The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
</pre>
</p> instead-->
<p>在无限的整数序列&nbsp;1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...中找到第&nbsp;<em>n&nbsp;</em>个数字。</p>

<p><strong>注意:</strong><br />
<em>n&nbsp;</em>是正数且在32为整形范围内&nbsp;(&nbsp;<em>n</em> &lt; 2<sup>31</sup>)。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
3

<strong>输出:</strong>
3
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong>
11

<strong>输出:</strong>
0

<strong>说明:</strong>
第11个数字在序列 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... 里是<strong>0</strong>，它是10的一部分。
</pre>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def findNthDigit(self, n):
        """
        :type n: int
        :rtype: int
        """
        digs = 0
        while True:
            digs += 1
            if n <= digs * (10**digs - 10**(digs-1)):
                break
        base = 10 ** (digs-1)
        surplus = n - sum((9 * 10 ** d * (d+1) for d in range(digs-1))) - 1
        return int(str(surplus//digs+base)[surplus%digs])

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/nth-digit/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/nth-digit/description/)

Solution: [LeetCode](https://leetcode.com/articles/nth-digit/)  /  [LeetCode中国](https://leetcode-cn.com/articles/nth-digit/)