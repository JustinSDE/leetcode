# 139. Word Break | 单词拆分

## Question description

<!--If you want to use the English description, use <p>Given a <strong>non-empty</strong> string <em>s</em> and a dictionary <em>wordDict</em> containing a list of <strong>non-empty</strong> words, determine if <em>s</em> can be segmented into a space-separated sequence of one or more dictionary words.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The same word in the dictionary may be reused multiple times in the segmentation.</li>
	<li>You may assume the dictionary does not contain duplicate words.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;, wordDict = [&quot;leet&quot;, &quot;code&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> Return true because <code>&quot;leetcode&quot;</code> can be segmented as <code>&quot;leet code&quot;</code>.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;applepenapple&quot;, wordDict = [&quot;apple&quot;, &quot;pen&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> Return true because <code>&quot;</code>applepenapple<code>&quot;</code> can be segmented as <code>&quot;</code>apple pen apple<code>&quot;</code>.
&nbsp;            Note that you are allowed to reuse a dictionary word.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;catsandog&quot;, wordDict = [&quot;cats&quot;, &quot;dog&quot;, &quot;sand&quot;, &quot;and&quot;, &quot;cat&quot;]
<strong>Output:</strong> false
</pre>
 instead-->
<p>给定一个<strong>非空</strong>字符串 <em>s</em> 和一个包含<strong>非空</strong>单词列表的字典 <em>wordDict</em>，判定&nbsp;<em>s</em> 是否可以被空格拆分为一个或多个在字典中出现的单词。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>拆分时可以重复使用字典中的单词。</li>
	<li>你可以假设字典中没有重复的单词。</li>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> s = &quot;leetcode&quot;, wordDict = [&quot;leet&quot;, &quot;code&quot;]
<strong>输出:</strong> true
<strong>解释:</strong> 返回 true 因为 &quot;leetcode&quot; 可以被拆分成 &quot;leet code&quot;。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> s = &quot;applepenapple&quot;, wordDict = [&quot;apple&quot;, &quot;pen&quot;]
<strong>输出:</strong> true
<strong>解释:</strong> 返回 true 因为 <code>&quot;</code>applepenapple<code>&quot;</code> 可以被拆分成 <code>&quot;</code>apple pen apple<code>&quot;</code>。
&nbsp;    注意你可以重复使用字典中的单词。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入:</strong> s = &quot;catsandog&quot;, wordDict = [&quot;cats&quot;, &quot;dog&quot;, &quot;sand&quot;, &quot;and&quot;, &quot;cat&quot;]
<strong>输出:</strong> false
</pre>


## Note

一开始想到递归，果不其然，TLE。

然后改成记忆化递归，结果因为用了类变量，而LeetCode是同一实例重复调用方法，结果出错。

于是，定义个函数用于递归，就解决了上面的问题。


## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: bool
        """
        cache = {}
        def warpper(_s, _wordDict):
            if _s in cache:
                return cache[_s]
            for w in _wordDict:
                if _s == w:
                    cache[_s] = True
                    return True
                elif _s.startswith(w):
                    if warpper(_s[len(w):], _wordDict):
                        cache[_s] = True
                        return True
            cache[_s] = False
            return False
        return warpper(s, wordDict)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/word-break/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-break/description/)

Solution: [LeetCode](https://leetcode.com/articles/word-break/)  /  [LeetCode中国](https://leetcode-cn.com/articles/word-break/)