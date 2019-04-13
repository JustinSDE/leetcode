# 5. Longest Palindromic Substring | 最长回文子串

## Question description

<!--If you want to use the English description, use <p>Given a string <strong>s</strong>, find the longest palindromic substring in <strong>s</strong>. You may assume that the maximum length of <strong>s</strong> is 1000.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> &quot;babad&quot;
<strong>Output:</strong> &quot;bab&quot;
<strong>Note:</strong> &quot;aba&quot; is also a valid answer.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> &quot;cbbd&quot;
<strong>Output:</strong> &quot;bb&quot;
</pre>
 instead-->
<p>给定一个字符串 <code>s</code>，找到 <code>s</code> 中最长的回文子串。你可以假设&nbsp;<code>s</code> 的最大长度为 1000。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> &quot;babad&quot;
<strong>输出:</strong> &quot;bab&quot;
<strong>注意:</strong> &quot;aba&quot; 也是一个有效答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> &quot;cbbd&quot;
<strong>输出:</strong> &quot;bb&quot;
</pre>


## Note

注意到回文串的一个特点：如果回文串长度大于1，则第一个字符与最后一个字符必然相等。

利用这个规律，我们可以记录各字符出现的位置，当出现重复字符时，才可能有长度大于1的回文串。

只需要看上一次出现该字符到当前位置之间的字符串是否为回文串即可。

先看长的字符串是否为回文串，如果长的是回文串，短的就不用看了。


## Solution

Language: **python3**  /  Runtime: 948 ms

```python3
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if not s:
            return ""
        d = collections.defaultdict(list)
        res = s[0]
        for i, c in enumerate(s):
            for j in d[c]:
                if i+1-j > len(res) and s[j:i+1] == s[j:i+1][::-1]:
                    res = s[j:i+1]
                    break
            d[c].append(i)
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-palindromic-substring/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-palindromic-substring/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-palindromic-substring/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-palindromic-substring/)