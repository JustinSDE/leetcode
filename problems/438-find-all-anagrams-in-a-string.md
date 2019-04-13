# 438. Find All Anagrams in a String | 找到字符串中所有字母异位词

## Question description

<!--If you want to use the English description, use <p>Given a string <b>s</b> and a <b>non-empty</b> string <b>p</b>, find all the start indices of <b>p</b>'s anagrams in <b>s</b>.</p>

<p>Strings consists of lowercase English letters only and the length of both strings <b>s</b> and <b>p</b> will not be larger than 20,100.</p>

<p>The order of output does not matter.</p>

<p><b>Example 1:</b>
<pre>
<b>Input:</b>
s: "cbaebabacd" p: "abc"

<b>Output:</b>
[0, 6]

<b>Explanation:</b>
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
</pre>
</p>

<p><b>Example 2:</b>
<pre>
<b>Input:</b>
s: "abab" p: "ab"

<b>Output:</b>
[0, 1, 2]

<b>Explanation:</b>
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
</pre>
</p> instead-->
<p>给定一个字符串&nbsp;<strong>s&nbsp;</strong>和一个非空字符串&nbsp;<strong>p</strong>，找到&nbsp;<strong>s&nbsp;</strong>中所有是&nbsp;<strong>p&nbsp;</strong>的字母异位词的子串，返回这些子串的起始索引。</p>

<p>字符串只包含小写英文字母，并且字符串&nbsp;<strong>s&nbsp;</strong>和 <strong>p&nbsp;</strong>的长度都不超过 20100。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>字母异位词指字母相同，但排列不同的字符串。</li>
	<li>不考虑答案输出的顺序。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong>
s: &quot;cbaebabacd&quot; p: &quot;abc&quot;

<strong>输出:</strong>
[0, 6]

<strong>解释:</strong>
起始索引等于 0 的子串是 &quot;cba&quot;, 它是 &quot;abc&quot; 的字母异位词。
起始索引等于 6 的子串是 &quot;bac&quot;, 它是 &quot;abc&quot; 的字母异位词。
</pre>

<p><strong>&nbsp;示例 2:</strong></p>

<pre>
<strong>输入:</strong>
s: &quot;abab&quot; p: &quot;ab&quot;

<strong>输出:</strong>
[0, 1, 2]

<strong>解释:</strong>
起始索引等于 0 的子串是 &quot;ab&quot;, 它是 &quot;ab&quot; 的字母异位词。
起始索引等于 1 的子串是 &quot;ba&quot;, 它是 &quot;ab&quot; 的字母异位词。
起始索引等于 2 的子串是 &quot;ab&quot;, 它是 &quot;ab&quot; 的字母异位词。
</pre>




## Solution

Language: **python3**  /  Runtime: 116 ms

```python3
class Solution:
    def findAnagrams(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: List[int]
        """
        if len(s) < len(p):
            return []
        res = []
        ph = sum(map(hash, list(p)))
        shs = list(map(hash, list(s)))
        sh = sum(shs[:len(p)])
        res = [0] if ph == sh else []
        for i in range(1, len(s)-len(p)+1):
            sh += (shs[i+len(p)-1] - shs[i-1])
            if ph == sh:
                res.append(i)
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-all-anagrams-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-all-anagrams-in-a-string/)