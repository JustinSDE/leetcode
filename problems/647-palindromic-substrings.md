# 647. Palindromic Substrings | 回文子串

## Question description

<!--If you want to use the English description, use <p>Given a string, your task is to count how many palindromic substrings in this string.</p>

<p>The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> &quot;abc&quot;
<b>Output:</b> 3
<b>Explanation:</b> Three palindromic strings: &quot;a&quot;, &quot;b&quot;, &quot;c&quot;.
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> &quot;aaa&quot;
<b>Output:</b> 6
<b>Explanation:</b> Six palindromic strings: &quot;a&quot;, &quot;a&quot;, &quot;a&quot;, &quot;aa&quot;, &quot;aa&quot;, &quot;aaa&quot;.
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The input string length won&#39;t exceed 1000.</li>
</ol>

<p>&nbsp;</p>
 instead-->
<p>给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。</p>

<p>具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被计为是不同的子串。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;abc&quot;
<strong>输出:</strong> 3
<strong>解释:</strong> 三个回文子串: &quot;a&quot;, &quot;b&quot;, &quot;c&quot;.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;aaa&quot;
<strong>输出:</strong> 6
<strong>说明:</strong> 6个回文子串: &quot;a&quot;, &quot;a&quot;, &quot;a&quot;, &quot;aa&quot;, &quot;aa&quot;, &quot;aaa&quot;.
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>输入的字符串长度不会超过1000。</li>
</ol>


## Note

这道题的运行时间居然达到了2060ms，看来方法还是比较暴力，需要考虑更优的做法。


## Solution

Language: **python3**  /  Runtime: 2060 ms

```python3
class Solution:
    def countSubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        dp = [0, 1]
        if len(s) < 2:
            return dp[len(s)]
        else:
            for i in range(2, len(s)+1):
                dp.append(dp[i-1] + [s[:i][j:] == s[:i][j:][::-1] for j in range(i)].count(True))
            return dp[-1]

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/palindromic-substrings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindromic-substrings/description/)

Solution: [LeetCode](https://leetcode.com/articles/palindromic-substrings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/palindromic-substrings/)