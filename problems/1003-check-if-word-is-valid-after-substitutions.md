# 1003. Check If Word Is Valid After Substitutions | 检查替换后的词是否有效

## Question description

<!--If you want to use the English description, use <p>We are given that the string <code>&quot;abc&quot;</code> is valid.</p>

<p>From any valid string <code>V</code>, we may split&nbsp;<code>V</code> into two pieces <code>X</code> and <code>Y</code> such that <code>X + Y</code> (<code>X</code> concatenated with <code>Y</code>) is equal to <code>V</code>.&nbsp; (<code>X</code> or <code>Y</code> may be empty.)&nbsp; Then, <code>X + &quot;abc&quot; + Y</code> is also valid.</p>

<p>If for example <code>S = &quot;abc&quot;</code>, then examples of valid strings are: <code>&quot;abc&quot;, &quot;aabcbc&quot;, &quot;abcabc&quot;, &quot;abcabcababcc&quot;</code>.&nbsp; Examples of <strong>invalid</strong>&nbsp;strings are: <code>&quot;abccba&quot;</code>, <code>&quot;ab&quot;</code>, <code>&quot;cababc&quot;</code>, <code>&quot;bac&quot;</code>.</p>

<p>Return <code>true</code> if and only if the given string&nbsp;<code>S</code>&nbsp;is valid.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;aabcbc&quot;</span>
<strong>Output: </strong><span id="example-output-1">true</span>
<strong>Explanation: </strong>
We start with the valid string &quot;abc&quot;.
Then we can insert another &quot;abc&quot; between &quot;a&quot; and &quot;bc&quot;, resulting in &quot;a&quot; + &quot;abc&quot; + &quot;bc&quot; which is &quot;aabcbc&quot;.
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;abcabcababcc&quot;</span>
<strong>Output: </strong><span id="example-output-2">true</span>
<strong>Explanation: </strong>
&quot;abcabcabc&quot; is valid after consecutive insertings of &quot;abc&quot;.
Then we can insert &quot;abc&quot; before the last letter, resulting in &quot;abcabcab&quot; + &quot;abc&quot; + &quot;c&quot; which is &quot;abcabcababcc&quot;.
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;abccba&quot;</span>
<strong>Output: </strong><span id="example-output-3">false</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">&quot;cababc&quot;</span>
<strong>Output: </strong><span id="example-output-4">false</span></pre>

<p>&nbsp;</p>
</div>
</div>
</div>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S[i]</code> is <code>&#39;a&#39;</code>, <code>&#39;b&#39;</code>, or <code>&#39;c&#39;</code></li>
</ol>

<div>
<div>
<div>
<div>&nbsp;</div>
</div>
</div>
</div> instead-->
<p>给定有效字符串&nbsp;<code>&quot;abc&quot;</code>。</p>

<p>对于任何有效的字符串 <code>V</code>，我们可以将 <code>V</code> 分成两个部分 <code>X</code> 和 <code>Y</code>，使得 <code>X + Y</code>（<code>X</code> 与 <code>Y</code> 连接）等于 <code>V</code>。（<code>X</code>&nbsp;或 <code>Y</code> 可以为空。）那么，<code>X + &quot;abc&quot; + Y</code> 也同样是有效的。</p>

<p>例如，如果 <code>S = &quot;abc&quot;</code>，则有效字符串的示例是：<code>&quot;abc&quot;</code>，<code>&quot;aabcbc&quot;</code>，<code>&quot;abcabc&quot;</code>，<code>&quot;abcabcababcc&quot;</code>。<strong>无效</strong>字符串的示例是：<code>&quot;abccba&quot;</code>，<code>&quot;ab&quot;</code>，<code>&quot;cababc&quot;</code>，<code>&quot;bac&quot;</code>。</p>

<p>如果给定字符串 <code>S</code> 有效，则返回 <code>true</code>；否则，返回 <code>false</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;aabcbc&quot;
<strong>输出：</strong>true
<strong>解释：</strong>
从有效字符串 &quot;abc&quot; 开始。
然后我们可以在 &quot;a&quot; 和 &quot;bc&quot; 之间插入另一个 &quot;abc&quot;，产生 &quot;a&quot; + &quot;abc&quot; + &quot;bc&quot;，即 &quot;aabcbc&quot;。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;abcabcababcc&quot;
<strong>输出：</strong>true
<strong>解释：</strong>
&quot;abcabcabc&quot; 是有效的，它可以视作在原串后连续插入 &quot;abc&quot;。
然后我们可以在最后一个字母之前插入 &quot;abc&quot;，产生 &quot;abcabcab&quot; + &quot;abc&quot; + &quot;c&quot;，即 &quot;abcabcababcc&quot;。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;abccba&quot;
<strong>输出：</strong>false
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>&quot;cababc&quot;
<strong>输出：</strong>false</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S[i]</code> 为&nbsp;<code>&#39;a&#39;</code>、<code>&#39;b&#39;</code>、或&nbsp;<code>&#39;c&#39;</code></li>
</ol>

<p>&nbsp;</p>




## Solution

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def isValid(self, S: str) -> bool:
        while 'abc' in S:
            S = S.replace('abc', '')
        return S == ''
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-word-is-valid-after-substitutions/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-word-is-valid-after-substitutions/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-word-is-valid-after-substitutions/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-word-is-valid-after-substitutions/)