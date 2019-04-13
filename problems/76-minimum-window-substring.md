# 76. Minimum Window Substring | 最小覆盖子串

## Question description

<!--If you want to use the English description, use <p>Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input: S</strong> = &quot;ADOBECODEBANC&quot;, <strong>T</strong> = &quot;ABC&quot;
<strong>Output:</strong> &quot;BANC&quot;
</pre>

<p><strong>Note:</strong></p>

<ul>
	<li>If there is no such window in S that covers all characters in T, return the empty string <code>&quot;&quot;</code>.</li>
	<li>If there is such window, you are guaranteed that there will always be only one unique minimum window in S.</li>
</ul> instead-->
<p>给定一个字符串 S 和一个字符串 T，请在 S 中找出包含 T 所有字母的最小子串。</p>

<p><strong>示例：</strong></p>

<pre><strong>输入: S</strong> = &quot;ADOBECODEBANC&quot;, <strong>T</strong> = &quot;ABC&quot;
<strong>输出:</strong> &quot;BANC&quot;</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>如果 S 中不存这样的子串，则返回空字符串 <code>&quot;&quot;</code>。</li>
	<li>如果 S 中存在这样的子串，我们保证它是唯一的答案。</li>
</ul>


## Note

利用快慢指针的技巧。初始时，快慢指针都在头部；如果快慢指针间子串覆盖T，就右移慢指针；否则就右移快指针。在指针移动过程中，更新快慢指针间子串的字符统计。每次找到覆盖T的子串时，如果子串短就暂存为结果。


## Solution

Language: **python3**  /  Runtime: 524 ms

```python3
class Solution:
    def minWindow(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        def cover(ac, bc):
            for bk, bv in bc.items():
                if ac[ord(bk)] < bv:
                    return False
            return True
        
        tc = collections.Counter(t)
        st, ed = 0, 0
        res = ""
        sc = [0] * 256
        while ed <= len(s):
            if cover(sc, tc):
                if not res or len(s[st:ed]) < len(res):
                    res = s[st:ed]
                sc[ord(s[st])] -= 1
                st += 1
            else:
                if ed < len(s):
                    sc[ord(s[ed])] += 1
                ed += 1
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-window-substring/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-window-substring/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-window-substring/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-window-substring/)