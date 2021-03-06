# 984. String Without AAA or BBB | 不含 AAA 或 BBB 的字符串

## Question description

<!--If you want to use the English description, use <p>Given two integers <code>A</code> and <code>B</code>, return <strong>any</strong> string <code>S</code> such that:</p>

<ul>
	<li><code>S</code> has length <code>A + B</code> and contains exactly <code>A</code> <code>&#39;a&#39;</code> letters, and exactly <code>B</code> <code>&#39;b&#39;</code> letters;</li>
	<li>The substring&nbsp;<code>&#39;aaa&#39;</code>&nbsp;does not occur in <code>S</code>;</li>
	<li>The substring <code>&#39;bbb&#39;</code> does not occur in <code>S</code>.</li>
</ul>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">1</span>, B = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">&quot;abb&quot;
</span><strong>Explanation:</strong> &quot;abb&quot;, &quot;bab&quot; and &quot;bba&quot; are all correct answers.
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-2-1">4</span>, B = <span id="example-input-2-2">1</span>
<strong>Output: </strong><span id="example-output-2">&quot;aabaa&quot;</span></pre>

<p>&nbsp;</p>
</div>

<p><strong>Note:</strong></p>

<ol>
	<li><code>0 &lt;= A &lt;= 100</code></li>
	<li><code>0 &lt;= B &lt;= 100</code></li>
	<li>It is guaranteed such an <code>S</code> exists for the given <code>A</code> and <code>B</code>.</li>
</ol>
 instead-->
<p>给定两个整数&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>，返回<strong>任意</strong>字符串 <code>S</code>，要求满足：</p>

<ul>
	<li><code>S</code> 的长度为&nbsp;<code>A + B</code>，且正好包含&nbsp;<code>A</code>&nbsp;个 <code>&#39;a&#39;</code>&nbsp;字母与&nbsp;<code>B</code>&nbsp;个 <code>&#39;b&#39;</code>&nbsp;字母；</li>
	<li>子串&nbsp;<code>&#39;aaa&#39;</code>&nbsp;没有出现在&nbsp;<code>S</code>&nbsp;中；</li>
	<li>子串&nbsp;<code>&#39;bbb&#39;</code> 没有出现在&nbsp;<code>S</code>&nbsp;中。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = 1, B = 2
<strong>输出：</strong>&quot;abb&quot;
<strong>解释：</strong>&quot;abb&quot;, &quot;bab&quot; 和 &quot;bba&quot; 都是正确答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = 4, B = 1
<strong>输出：</strong>&quot;aabaa&quot;</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= A &lt;= 100</code></li>
	<li><code>0 &lt;= B &lt;= 100</code></li>
	<li>对于给定的 <code>A</code> 和 <code>B</code>，保证存在满足要求的 <code>S</code>。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public String strWithout3a3b(int A, int B) {
        if (A == 0) {
            return new String(new char[B]).replace('\0', 'b');
        }
        if (B == 0) {
            return new String(new char[A]).replace('\0', 'a');
        }
        if (A == B) {
            return new String(new char[A * 2]).replace("\0\0", "ab");
        } else {
            if (A > B) {
                return "aab" + strWithout3a3b(A - 2, B - 1);
            } else {
                return "bba" + strWithout3a3b(A - 1, B - 2);
            }
        }
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/string-without-aaa-or-bbb/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-without-aaa-or-bbb/description/)

Solution: [LeetCode](https://leetcode.com/articles/string-without-aaa-or-bbb/)  /  [LeetCode中国](https://leetcode-cn.com/articles/string-without-aaa-or-bbb/)