# 893. Groups of Special-Equivalent Strings | 特殊等价字符串组

## Question description

<!--If you want to use the English description, use <p>You are given an array <code>A</code> of strings.</p>

<p>Two strings <code>S</code> and <code>T</code> are&nbsp;<em>special-equivalent</em>&nbsp;if after any number of <em>moves</em>, S == T.</p>

<p>A <em>move</em> consists of choosing two indices <code>i</code> and <code>j</code> with <code>i % 2 == j % 2</code>, and swapping <code>S[i]</code> with <code>S[j]</code>.</p>

<p>Now, a <em>group of special-equivalent strings from <code>A</code></em>&nbsp;is a&nbsp;non-empty subset S of <code>A</code>&nbsp;such that any string not in S&nbsp;is not special-equivalent with any string in S.</p>

<p>Return the number of groups of special-equivalent strings from <code>A</code>.</p>

<p>&nbsp;</p>

<ul>
</ul>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[&quot;a&quot;,&quot;b&quot;,&quot;c&quot;,&quot;a&quot;,&quot;c&quot;,&quot;c&quot;]</span>
<strong>Output: </strong><span id="example-output-1">3</span>
<span><strong>Explanation</strong>: 3 groups [&quot;a&quot;,&quot;a&quot;], [&quot;b&quot;], [&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[&quot;aa&quot;,&quot;bb&quot;,&quot;ab&quot;,&quot;ba&quot;]</span>
<strong>Output: </strong><span id="example-output-2">4</span>
<strong>Explanation</strong>: 4 groups <span id="example-input-2-1">[&quot;aa&quot;], [&quot;bb&quot;], [&quot;ab&quot;], [&quot;ba&quot;]</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[&quot;abc&quot;,&quot;acb&quot;,&quot;bac&quot;,&quot;bca&quot;,&quot;cab&quot;,&quot;cba&quot;]</span>
<strong>Output: </strong><span id="example-output-3">3</span>
<strong>Explanation</strong>: 3 groups [&quot;abc&quot;,&quot;cba&quot;], [&quot;acb&quot;,&quot;bca&quot;], [&quot;bac&quot;,&quot;cab&quot;]
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">[&quot;abcd&quot;,&quot;cdab&quot;,&quot;adcb&quot;,&quot;cbad&quot;]</span>
<strong>Output: </strong><span id="example-output-4">1</span>
<strong>Explanation</strong>: 1 group <span id="example-input-4-1">[&quot;abcd&quot;,&quot;cdab&quot;,&quot;adcb&quot;,&quot;cbad&quot;]</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li><code>1 &lt;= A.length &lt;= 1000</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 20</code></li>
	<li>All <code>A[i]</code> have the same length.</li>
	<li>All <code>A[i]</code> consist of only lowercase letters.</li>
</ul>
</div>
</div>
</div>
</div>
 instead-->
<p>你将得到一个字符串数组 <code>A</code>。</p>

<p>如果经过任意次数的移动，S == T，那么两个字符串 <code>S</code> 和 <code>T</code> 是<em>特殊等价</em>的。</p>

<p>&nbsp;</p>

<p>一次<em>移动</em>包括选择两个索引 <code>i</code> 和 <code>j</code>，且&nbsp;<code>i％2 == j％2</code>，并且交换 <code>S[j]</code> 和 <code>S [i]</code>。</p>

<p>现在规定，<em><code>A</code> 中的特殊等价字符串组</em>是 <code>A</code> 的非空子集 <code>S</code>，这样不在 <code>S</code> 中的任何字符串与 <code>S</code> 中的任何字符串都不是特殊等价的。</p>

<p>&nbsp;</p>

<p>返回 <code>A</code>&nbsp;中特殊等价字符串组的数量。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[&quot;a&quot;,&quot;b&quot;,&quot;c&quot;,&quot;a&quot;,&quot;c&quot;,&quot;c&quot;]
<strong>输出：</strong>3
<strong>解释：</strong>3<strong> </strong>组 [&quot;a&quot;,&quot;a&quot;]，[&quot;b&quot;]，[&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[&quot;aa&quot;,&quot;bb&quot;,&quot;ab&quot;,&quot;ba&quot;]
<strong>输出：</strong>4
<strong>解释：</strong>4 组 [&quot;aa&quot;]，[&quot;bb&quot;]，[&quot;ab&quot;]，[&quot;ba&quot;]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[&quot;abc&quot;,&quot;acb&quot;,&quot;bac&quot;,&quot;bca&quot;,&quot;cab&quot;,&quot;cba&quot;]
<strong>输出：</strong>3
<strong>解释：</strong>3 组 [&quot;abc&quot;,&quot;cba&quot;]，[&quot;acb&quot;,&quot;bca&quot;]，[&quot;bac&quot;,&quot;cab&quot;]
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[&quot;abcd&quot;,&quot;cdab&quot;,&quot;adcb&quot;,&quot;cbad&quot;]
<strong>输出：</strong>1
<strong>解释：</strong>1 组 [&quot;abcd&quot;,&quot;cdab&quot;,&quot;adcb&quot;,&quot;cbad&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= A.length &lt;= 1000</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 20</code></li>
	<li>所有&nbsp;<code>A[i]</code>&nbsp;都具有相同的长度。</li>
	<li>所有&nbsp;<code>A[i]</code>&nbsp;都只由小写字母组成。</li>
</ul>


## Note

字符串特征向量法


## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def numSpecialEquivGroups(self, A):
        """
        :type A: List[str]
        :rtype: int
        """
        return len({tuple(sorted(s[0::2]) + sorted(s[1::2])) for s in A})
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/groups-of-special-equivalent-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/groups-of-special-equivalent-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/groups-of-special-equivalent-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/groups-of-special-equivalent-strings/)