# 387. First Unique Character in a String | 字符串中的第一个唯一字符

## Question description

<!--If you want to use the English description, use <p>
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.
</p>
<p><b>Examples:</b>
<pre>
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
</pre>
</p>

<p>
<b>Note:</b> You may assume the string contain only lowercase letters.
</p> instead-->
<p>给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。</p>

<p><strong>案例:</strong></p>

<pre>
s = &quot;leetcode&quot;
返回 0.

s = &quot;loveleetcode&quot;,
返回 2.
</pre>

<p>&nbsp;</p>

<p><strong>注意事项：</strong>您可以假定该字符串只包含小写字母。</p>




## Solution

Language: **python3**  /  Runtime: 208 ms

```python3
class Solution:
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        d = collections.OrderedDict()
        for c in s:
            d[c] = d.get(c, 0) + 1
        for c, n in d.items():
            if n == 1:
                return s.index(c)
        return -1
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/first-unique-character-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-unique-character-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/first-unique-character-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/first-unique-character-in-a-string/)