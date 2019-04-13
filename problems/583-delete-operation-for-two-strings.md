# 583. Delete Operation for Two Strings | 两个字符串的删除操作

## Question description

<!--If you want to use the English description, use <p>
Given two words <i>word1</i> and <i>word2</i>, find the minimum number of steps required to make <i>word1</i> and <i>word2</i> the same, where in each step you can delete one character in either string.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> "sea", "eat"
<b>Output:</b> 2
<b>Explanation:</b> You need one step to make "sea" to "ea" and another step to make "eat" to "ea".
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The length of given words won't exceed 500.</li>
<li>Characters in given words can only be lower-case letters.</li>
</ol>
</p> instead-->
<p>给定两个单词&nbsp;<em>word1&nbsp;</em>和&nbsp;<em>word2</em>，找到使得&nbsp;<em>word1&nbsp;</em>和&nbsp;<em>word2&nbsp;</em>相同所需的最小步数，每步可以删除任意一个字符串中的一个字符。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;sea&quot;, &quot;eat&quot;
<strong>输出:</strong> 2
<strong>解释:</strong> 第一步将&quot;sea&quot;变为&quot;ea&quot;，第二步将&quot;eat&quot;变为&quot;ea&quot;
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>给定单词的长度不超过500。</li>
	<li>给定单词中的字符只含有小写字母。</li>
</ol>


## Note

两个单词的长度减去两倍的LCS即可。

LCS是很经典的问题，务必熟知！

LCS: 最长公共子序列


## Solution

Language: **python3**  /  Runtime: 584 ms

```python3
class Solution:
    def CLS(self, s1, s2):
        dp = [[0] * (len(s2)+1) for _ in range(len(s1)+1)]
        for i in range(1, len(s1)+1):
            for j in range(1, len(s2)+1):
                if s1[i-1] == s2[j-1]:
                    dp[i][j] = 1 + dp[i-1][j-1]
                else:
                    dp[i][j] = max(dp[i-1][j], dp[i][j-1])
        return dp[-1][-1]

    def minDistance(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: int
        """
        return len(word1) + len(word2) - 2 * self.CLS(word1, word2)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/delete-operation-for-two-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/delete-operation-for-two-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/delete-operation-for-two-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/delete-operation-for-two-strings/)