# 896. Monotonic Array | 单调数列

## Question description

<!--If you want to use the English description, use <p>An array is <em>monotonic</em> if it is either monotone increasing or monotone decreasing.</p>

<p>An array <code>A</code> is monotone increasing if for all <code>i &lt;= j</code>, <code>A[i] &lt;= A[j]</code>.&nbsp; An array <code>A</code> is monotone decreasing if for all <code>i &lt;= j</code>, <code>A[i] &gt;= A[j]</code>.</p>

<p>Return <code>true</code> if and only if the given array <code>A</code> is monotonic.</p>

<p>&nbsp;</p>

<ol>
</ol>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,2,3]</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[6,5,4,4]</span>
<strong>Output: </strong><span id="example-output-2">true</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[1,3,2]</span>
<strong>Output: </strong><span id="example-output-3">false</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">[1,2,4,5]</span>
<strong>Output: </strong><span id="example-output-4">true</span>
</pre>

<div>
<p><strong>Example 5:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-5-1">[1,1,1]</span>
<strong>Output: </strong><span id="example-output-5">true</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 50000</code></li>
	<li><code>-100000 &lt;= A[i] &lt;= 100000</code></li>
</ol>
</div>
</div>
</div>
</div>
</div>
 instead-->
<p>如果数组是单调递增或单调递减的，那么它是<em>单调的</em>。</p>

<p>如果对于所有 <code>i &lt;= j</code>，<code>A[i] &lt;= A[j]</code>，那么数组 <code>A</code> 是单调递增的。 如果对于所有 <code>i &lt;= j</code>，<code>A[i]&gt; = A[j]</code>，那么数组 <code>A</code> 是单调递减的。</p>

<p>当给定的数组 <code>A</code>&nbsp;是单调数组时返回 <code>true</code>，否则返回 <code>false</code>。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[1,2,2,3]
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[6,5,4,4]
<strong>输出：</strong>true
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[1,3,2]
<strong>输出：</strong>false
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[1,2,4,5]
<strong>输出：</strong>true
</pre>

<p><strong>示例&nbsp;5：</strong></p>

<pre><strong>输入：</strong>[1,1,1]
<strong>输出：</strong>true
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 50000</code></li>
	<li><code>-100000 &lt;= A[i] &lt;= 100000</code></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 224 ms

```python3
class Solution:
    def isMonotonic(self, A):
        """
        :type A: List[int]
        :rtype: bool
        """
        return A == sorted(A) or A == sorted(A, reverse=True)
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/monotonic-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/monotonic-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/monotonic-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/monotonic-array/)