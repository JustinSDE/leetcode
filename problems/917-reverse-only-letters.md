# 917. Reverse Only Letters | 仅仅反转字母

## Question description

<!--If you want to use the English description, use <p>Given a string <code>S</code>, return the &quot;reversed&quot; string where all characters that are not a letter&nbsp;stay in the same place, and all letters reverse their positions.</p>

<p>&nbsp;</p>

<div>
<div>
<div>
<ol>
</ol>
</div>
</div>
</div>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;ab-cd&quot;</span>
<strong>Output: </strong><span id="example-output-1">&quot;dc-ba&quot;</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;a-bC-dEf-ghIj&quot;</span>
<strong>Output: </strong><span id="example-output-2">&quot;j-Ih-gfE-dCba&quot;</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;Test1ng-Leet=code-Q!&quot;</span>
<strong>Output: </strong><span id="example-output-3">&quot;Qedo1ct-eeLg=ntse-T!&quot;</span>
</pre>

<p>&nbsp;</p>

<div>
<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>S.length &lt;= 100</code></li>
	<li><code>33 &lt;= S[i].ASCIIcode &lt;= 122</code>&nbsp;</li>
	<li><code>S</code> doesn&#39;t contain <code>\</code> or <code>&quot;</code></li>
</ol>
</div>
</div>
</div>
</div> instead-->
<p>给定一个字符串&nbsp;<code>S</code>，返回&nbsp;&ldquo;反转后的&rdquo;&nbsp;字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;ab-cd&quot;
<strong>输出：</strong>&quot;dc-ba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;a-bC-dEf-ghIj&quot;
<strong>输出：</strong>&quot;j-Ih-gfE-dCba&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;Test1ng-Leet=code-Q!&quot;
<strong>输出：</strong>&quot;Qedo1ct-eeLg=ntse-T!&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>S.length &lt;= 100</code></li>
	<li><code>33 &lt;= S[i].ASCIIcode &lt;= 122</code>&nbsp;</li>
	<li><code>S</code> 中不包含&nbsp;<code>\</code> or <code>&quot;</code></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def reverseOnlyLetters(self, S):
        """
        :type S: str
        :rtype: str
        """
        t = list(S)
        i, j = 0, len(t) - 1
        while i < j:
            while i < j and not t[i].isalpha():
                i += 1
            while i < j and not t[j].isalpha():
                j -= 1
            t[i], t[j] = t[j], t[i]
            i += 1
            j -= 1
        return ''.join(t)

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-only-letters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-only-letters/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-only-letters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-only-letters/)