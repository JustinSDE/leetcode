# 537. Complex Number Multiplication | 复数乘法

## Question description

<!--If you want to use the English description, use <p>
Given two strings representing two <a href = "https://en.wikipedia.org/wiki/Complex_number">complex numbers</a>.</p>

<p>
You need to return a string representing their multiplication. Note i<sup>2</sup> = -1 according to the definition.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> "1+1i", "1+1i"
<b>Output:</b> "0+2i"
<b>Explanation:</b> (1 + i) * (1 + i) = 1 + i<sup>2</sup> + 2 * i = 2i, and you need convert it to the form of 0+2i.
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> "1+-1i", "1+-1i"
<b>Output:</b> "0+-2i"
<b>Explanation:</b> (1 - i) * (1 - i) = 1 + i<sup>2</sup> - 2 * i = -2i, and you need convert it to the form of 0+-2i.
</pre>
</p>

<p><b>Note:</b>
<ol>
<li>The input strings will not have extra blank.</li>
<li>The input strings will be given in the form of <b>a+bi</b>, where the integer <b>a</b> and <b>b</b> will both belong to the range of [-100, 100]. And <b>the output should be also in this form</b>.</li>
</ol>
</p> instead-->
<p>给定两个表示<a href="https://baike.baidu.com/item/%E5%A4%8D%E6%95%B0/254365?fr=aladdin">复数</a>的字符串。</p>

<p>返回表示它们乘积的字符串。注意，根据定义 i<sup>2</sup> = -1 。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;1+1i&quot;, &quot;1+1i&quot;
<strong>输出:</strong> &quot;0+2i&quot;
<strong>解释:</strong> (1 + i) * (1 + i) = 1 + i<sup>2</sup> + 2 * i = 2i ，你需要将它转换为 0+2i 的形式。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;1+-1i&quot;, &quot;1+-1i&quot;
<strong>输出:</strong> &quot;0+-2i&quot;
<strong>解释:</strong> (1 - i) * (1 - i) = 1 + i<sup>2</sup> - 2 * i = -2i ，你需要将它转换为 0+-2i 的形式。 
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>输入字符串不包含额外的空格。</li>
	<li>输入字符串将以&nbsp;<strong>a+bi</strong> 的形式给出，其中整数 <strong>a</strong> 和 <strong>b</strong> 的范围均在 [-100, 100] 之间。<strong>输出也应当符合这种形式</strong>。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def complexNumberMultiply(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        a1, b1 = map(int, a[:-1].split('+'))
        a2, b2 = map(int, b[:-1].split('+'))
        return '%d+%di' % (a1*a2-b1*b2, a1*b2+a2*b1)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/complex-number-multiplication/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/complex-number-multiplication/description/)

Solution: [LeetCode](https://leetcode.com/articles/complex-number-multiplication/)  /  [LeetCode中国](https://leetcode-cn.com/articles/complex-number-multiplication/)