# 290. Word Pattern | 单词模式

## Question description

<!--If you want to use the English description, use <p>Given a <code>pattern</code> and a string <code>str</code>, find if <code>str</code> follows the same pattern.</p>

<p>Here <b>follow</b> means a full match, such that there is a bijection between a letter in <code>pattern</code> and a <b>non-empty</b> word in <code>str</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> true</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat fish&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;aaaa&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog dog dog dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><b>Notes:</b><br />
You may assume <code>pattern</code> contains only lowercase letters, and <code>str</code> contains lowercase letters that may be separated by a single space.</p>
 instead-->
<p>给定一种 <code>pattern(模式)</code>&nbsp;和一个字符串&nbsp;<code>str</code>&nbsp;，判断 <code>str</code> 是否遵循相同的模式。</p>

<p>这里的<strong>遵循</strong>指完全匹配，例如，&nbsp;<code>pattern</code>&nbsp;里的每个字母和字符串&nbsp;<code>str</code><strong>&nbsp;</strong>中的每个非空单词之间存在着双向连接的对应模式。</p>

<p><strong>示例1:</strong></p>

<pre><strong>输入:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>输出:</strong> true</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat fish&quot;</code>
<strong>输出:</strong> false</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> pattern = <code>&quot;aaaa&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>输出:</strong> false</pre>

<p><strong>示例&nbsp;4:</strong></p>

<pre><strong>输入:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog dog dog dog&quot;</code>
<strong>输出:</strong> false</pre>

<p><strong>说明:</strong><br>
你可以假设&nbsp;<code>pattern</code>&nbsp;只包含小写字母，&nbsp;<code>str</code>&nbsp;包含了由单个空格分隔的小写字母。&nbsp; &nbsp;&nbsp;</p>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def wordPattern(self, pattern, str):
        """
        :type pattern: str
        :type str: str
        :rtype: bool
        """
        b = str.split()
        if len(pattern) != len(b):
            return False
        d = dict()
        s = set()
        for x, y in zip(pattern, b):
            if x in d:
                if d[x] != y:
                    return False
            else:
                if y in s:
                    return False
                else:
                    d[x] = y
                    s.add(y)
        return True
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/word-pattern/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-pattern/description/)

Solution: [LeetCode](https://leetcode.com/articles/word-pattern/)  /  [LeetCode中国](https://leetcode-cn.com/articles/word-pattern/)