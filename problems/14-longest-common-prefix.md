# 14. Longest Common Prefix | 最长公共前缀

## Question description

<!--If you want to use the English description, use <p>Write a function to find the longest common prefix string amongst an array of strings.</p>

<p>If there is no common prefix, return an empty string <code>&quot;&quot;</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>[&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>Output:</strong> &quot;fl&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>[&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>Output:</strong> &quot;&quot;
<strong>Explanation:</strong> There is no common prefix among the input strings.
</pre>

<p><strong>Note:</strong></p>

<p>All given inputs are in lowercase letters <code>a-z</code>.</p>
 instead-->
<p>编写一个函数来查找字符串数组中的最长公共前缀。</p>

<p>如果不存在公共前缀，返回空字符串&nbsp;<code>&quot;&quot;</code>。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>[&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>输出:</strong> &quot;fl&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>[&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>输出:</strong> &quot;&quot;
<strong>解释:</strong> 输入不存在公共前缀。
</pre>

<p><strong>说明:</strong></p>

<p>所有输入只包含小写字母&nbsp;<code>a-z</code>&nbsp;。</p>


## Note

这题很简单，但是容易考虑不周全字符串索引存在性问题。


## Solution

Language: **python3**  /  Runtime: 52 ms

```python3
class Solution:
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        rst = ''
        i = 0
        while True:
            c = []
            for s in strs:
                if len(s) > i:
                    c.append(s[i])
                else:
                    return rst
            c = set(c)
            if len(c) == 1:
                rst += list(c)[0]
                i += 1
            else:
                break
        return rst

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-common-prefix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-common-prefix/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-common-prefix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-common-prefix/)