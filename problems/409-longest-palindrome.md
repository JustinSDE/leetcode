# 409. Longest Palindrome | 最长回文串

## Question description

<!--If you want to use the English description, use <p>Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.</p>

<p>This is case sensitive, for example <code>"Aa"</code> is not considered a palindrome here.</p>

<p><b>Note:</b><br />
Assume the length of given string will not exceed 1,010.
</p>

<p><b>Example: </b>
<pre>
Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.
</pre>
</p> instead-->
<p>给定一个包含大写字母和小写字母的字符串，找到通过这些字母构造成的最长的回文串。</p>

<p>在构造过程中，请注意区分大小写。比如&nbsp;<code>&quot;Aa&quot;</code>&nbsp;不能当做一个回文字符串。</p>

<p><strong>注意:</strong><br />
假设字符串的长度不会超过 1010。</p>

<p><strong>示例 1: </strong></p>

<pre>
输入:
&quot;abccccdd&quot;

输出:
7

解释:
我们可以构造的最长的回文串是&quot;dccaccd&quot;, 它的长度是 7。
</pre>




## Solution

Language: **python3**  /  Runtime: 68 ms

```python3
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """
        res = 0
        for n in collections.Counter(s).values():
            res += n - int(n % 2)
        return res + int(res < len(s))

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-palindrome/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-palindrome/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-palindrome/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-palindrome/)