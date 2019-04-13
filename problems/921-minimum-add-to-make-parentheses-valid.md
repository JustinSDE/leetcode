# 921. Minimum Add to Make Parentheses Valid | 使括号有效的最少添加

## Question description

<!--If you want to use the English description, use <p>Given a string&nbsp;<code>S</code> of <code>&#39;(&#39;</code> and <code>&#39;)&#39;</code> parentheses, we add the minimum number of parentheses ( <code>&#39;(&#39;</code> or <code>&#39;)&#39;</code>, and in any positions ) so that the resulting parentheses string is valid.</p>

<p>Formally, a parentheses string is valid if and only if:</p>

<ul>
	<li>It is the empty string, or</li>
	<li>It can be written as <code>AB</code>&nbsp;(<code>A</code> concatenated with <code>B</code>), where <code>A</code> and <code>B</code> are valid strings, or</li>
	<li>It can be written as <code>(A)</code>, where <code>A</code> is a valid string.</li>
</ul>

<p>Given a parentheses string, return the minimum number of parentheses we must add to make the resulting string valid.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;())&quot;</span>
<strong>Output: </strong><span id="example-output-1">1</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;(((&quot;</span>
<strong>Output: </strong><span id="example-output-2">3</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;()&quot;</span>
<strong>Output: </strong><span id="example-output-3">0</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">&quot;()))((&quot;</span>
<strong>Output: </strong><span id="example-output-4">4</span></pre>

<p>&nbsp;</p>
</div>
</div>
</div>

<p><strong>Note:</strong></p>

<ol>
	<li><code>S.length &lt;= 1000</code></li>
	<li><code>S</code> only consists of <code>&#39;(&#39;</code> and <code>&#39;)&#39;</code> characters.</li>
</ol>

<div>
<div>
<div>
<div>&nbsp;</div>
</div>
</div>
</div> instead-->
<p>给定一个由&nbsp;<code>&#39;(&#39;</code>&nbsp;和&nbsp;<code>&#39;)&#39;</code>&nbsp;括号组成的字符串 <code>S</code>，我们需要添加最少的括号（ <code>&#39;(&#39;</code>&nbsp;或是&nbsp;<code>&#39;)&#39;</code>，可以在任何位置），以使得到的括号字符串有效。</p>

<p>从形式上讲，只有满足下面几点之一，括号字符串才是有效的：</p>

<ul>
	<li>它是一个空字符串，或者</li>
	<li>它可以被写成&nbsp;<code>AB</code>&nbsp;（<code>A</code>&nbsp;与&nbsp;<code>B</code>&nbsp;连接）, 其中&nbsp;<code>A</code> 和&nbsp;<code>B</code>&nbsp;都是有效字符串，或者</li>
	<li>它可以被写作&nbsp;<code>(A)</code>，其中&nbsp;<code>A</code>&nbsp;是有效字符串。</li>
</ul>

<p>给定一个括号字符串，返回为使结果字符串有效而必须添加的最少括号数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;())&quot;
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;(((&quot;
<strong>输出：</strong>3
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;()&quot;
<strong>输出：</strong>0
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>&quot;()))((&quot;
<strong>输出：</strong>4</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>S.length &lt;= 1000</code></li>
	<li><code>S</code> 只包含&nbsp;<code>&#39;(&#39;</code> 和&nbsp;<code>&#39;)&#39;</code>&nbsp;字符。</li>
</ol>

<p>&nbsp;</p>




## Solution

Language: **python3**  /  Runtime: 176 ms

```python3
class Solution:
    def minAddToMakeValid(self, S):
        """
        :type S: str
        :rtype: int
        """
        s = list(S)
        i = 1
        ln, rn = 0, 0
        res = 0
        while i <= len(s):
            ln = s[:i].count("(")
            rn = s[:i].count(")")
            for _ in range(rn - ln):
                s.insert(0, "(")
                i += 1
                res += 1
            i += 1
        res += s.count("(") - s.count(")")
        return res
            
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-add-to-make-parentheses-valid/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-add-to-make-parentheses-valid/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-add-to-make-parentheses-valid/)