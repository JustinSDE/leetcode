# 821. Shortest Distance to a Character | 字符的最短距离

## Question description

<!--If you want to use the English description, use <p>Given a string <code>S</code>&nbsp;and a character <code>C</code>, return an array of integers representing the shortest distance from the character <code>C</code> in the string.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> S = &quot;loveleetcode&quot;, C = &#39;e&#39;
<strong>Output:</strong> [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>S</code> string length is&nbsp;in&nbsp;<code>[1, 10000].</code></li>
	<li><code>C</code>&nbsp;is a single character, and guaranteed to be in string <code>S</code>.</li>
	<li>All letters in <code>S</code> and <code>C</code> are lowercase.</li>
</ol>
 instead-->
<p>给定一个字符串&nbsp;<code>S</code>&nbsp;和一个字符&nbsp;<code>C</code>。返回一个代表字符串&nbsp;<code>S</code>&nbsp;中每个字符到字符串&nbsp;<code>S</code>&nbsp;中的字符&nbsp;<code>C</code>&nbsp;的最短距离的数组。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> S = &quot;loveleetcode&quot;, C = &#39;e&#39;
<strong>输出:</strong> [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>字符串&nbsp;<code>S</code>&nbsp;的长度范围为&nbsp;<code>[1, 10000]</code>。</li>
	<li><code>C</code>&nbsp;是一个单字符，且保证是字符串&nbsp;<code>S</code>&nbsp;里的字符。</li>
	<li><code>S</code>&nbsp;和&nbsp;<code>C</code>&nbsp;中的所有字母均为小写字母。</li>
</ol>


## Note

这题比较简单，先记录C出现的位置，然后再次扫描S，计算与左侧C和右侧C的最小间隔，主要难点在于边界的处理。可以把一个很小和很大的数分别插入到C出现位置数组的两端，这样就可以不额外处理边界了，代码会优雅点。


## Solution

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def shortestToChar(self, S, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        cps = [-1 * len(S)]
        cps.extend([i for i, s in enumerate(S) if s == C])
        cps.append(2 * len(S))
        p = 1
        res = []
        for i, s in enumerate(S):
            if i < cps[p]:
                res.append(min( i - cps[p-1] , cps[p] - i ))
            else:
                p += 1
                res.append(0)
        return res
                
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shortest-distance-to-a-character/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shortest-distance-to-a-character/description/)

Solution: [LeetCode](https://leetcode.com/articles/shortest-distance-to-a-character/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shortest-distance-to-a-character/)