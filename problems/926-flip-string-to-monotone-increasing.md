# 926. Flip String to Monotone Increasing | 将字符串翻转到单调递增

## Question description

<!--If you want to use the English description, use <p>A string of <code>&#39;0&#39;</code>s and <code>&#39;1&#39;</code>s is <em>monotone increasing</em> if it consists of some number of <code>&#39;0&#39;</code>s (possibly 0), followed by some number of <code>&#39;1&#39;</code>s (also possibly 0.)</p>

<p>We are given a string <code>S</code> of <code>&#39;0&#39;</code>s and <code>&#39;1&#39;</code>s, and we may flip any <code>&#39;0&#39;</code> to a <code>&#39;1&#39;</code> or a <code>&#39;1&#39;</code> to a <code>&#39;0&#39;</code>.</p>

<p>Return the minimum number of flips to make <code>S</code>&nbsp;monotone increasing.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;00110&quot;</span>
<strong>Output: </strong><span id="example-output-1">1</span>
<strong>Explanation: </strong>We flip the last digit to get 00111.
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;010110&quot;</span>
<strong>Output: </strong><span id="example-output-2">2</span>
<strong>Explanation: </strong>We flip to get 011111, or alternatively 000111.
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;00011000&quot;</span>
<strong>Output: </strong><span id="example-output-3">2</span>
<strong>Explanation: </strong>We flip to get 00000000.
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S</code> only consists of <code>&#39;0&#39;</code> and <code>&#39;1&#39;</code> characters.</li>
</ol>
</div>
</div>
</div> instead-->
<p>如果一个由&nbsp;<code>&#39;0&#39;</code> 和 <code>&#39;1&#39;</code>&nbsp;组成的字符串，是以一些 <code>&#39;0&#39;</code>（可能没有 <code>&#39;0&#39;</code>）后面跟着一些 <code>&#39;1&#39;</code>（也可能没有 <code>&#39;1&#39;</code>）的形式组成的，那么该字符串是<em>单调递增</em>的。</p>

<p>我们给出一个由字符 <code>&#39;0&#39;</code> 和 <code>&#39;1&#39;</code>&nbsp;组成的字符串&nbsp;<code>S</code>，我们可以将任何&nbsp;<code>&#39;0&#39;</code> 翻转为&nbsp;<code>&#39;1&#39;</code>&nbsp;或者将&nbsp;<code>&#39;1&#39;</code>&nbsp;翻转为&nbsp;<code>&#39;0&#39;</code>。</p>

<p>返回使 <code>S</code> 单调递增的最小翻转次数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;00110&quot;
<strong>输出：</strong>1
<strong>解释：</strong>我们翻转最后一位得到 00111.
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;010110&quot;
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 011111，或者是 000111。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;00011000&quot;
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 00000000。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S</code> 中只包含字符&nbsp;<code>&#39;0&#39;</code>&nbsp;和&nbsp;<code>&#39;1&#39;</code></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 64 ms

```python3
class Solution:
    def minFlipsMonoIncr(self, S):
        """
        :type S: str
        :rtype: int
        """
        a = S.count('0')
        b = S.count('1')
        if a == 0 or b == 0:
            return 0
        dp = [0] * (a+b+1)
        dp[0] = a
        lf = 0
        rf = a
        for i, s in enumerate(S):
            if s == '1':
                lf += 1
            else:
                rf -= 1
            dp[i+1] = lf + rf
        return min(dp)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/flip-string-to-monotone-increasing/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flip-string-to-monotone-increasing/description/)

Solution: [LeetCode](https://leetcode.com/articles/flip-string-to-monotone-increasing/)  /  [LeetCode中国](https://leetcode-cn.com/articles/flip-string-to-monotone-increasing/)