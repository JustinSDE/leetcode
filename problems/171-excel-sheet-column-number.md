# 171. Excel Sheet Column Number | Excel表列序号

## Question description

<!--If you want to use the English description, use <p>Given a column title as appear in an Excel sheet, return its corresponding column number.</p>

<p>For example:</p>

<pre>
    A -&gt; 1
    B -&gt; 2
    C -&gt; 3
    ...
    Z -&gt; 26
    AA -&gt; 27
    AB -&gt; 28 
    ...
</pre>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> &quot;A&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>&quot;AB&quot;
<strong>Output:</strong> 28
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>&quot;ZY&quot;
<strong>Output:</strong> 701
</pre> instead-->
<p>给定一个Excel表格中的列名称，返回其相应的列序号。</p>

<p>例如，</p>

<pre>    A -&gt; 1
    B -&gt; 2
    C -&gt; 3
    ...
    Z -&gt; 26
    AA -&gt; 27
    AB -&gt; 28 
    ...
</pre>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;A&quot;
<strong>输出:</strong> 1
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>&quot;AB&quot;
<strong>输出:</strong> 28
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入: </strong>&quot;ZY&quot;
<strong>输出:</strong> 701</pre>

<p><strong>致谢：</strong><br>
特别感谢&nbsp;<a href="http://leetcode.com/discuss/user/ts">@ts</a>&nbsp;添加此问题并创建所有测试用例。</p>




## Solution

Language: **python3**  /  Runtime: 60 ms

```python3
class Solution:
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        res = 0
        for c in s:
            res = 26 * res + ord(c) - ord('A') + 1
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/excel-sheet-column-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/excel-sheet-column-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/excel-sheet-column-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/excel-sheet-column-number/)