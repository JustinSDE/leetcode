# 389. Find the Difference | 找不同

## Question description

<!--If you want to use the English description, use <p>
Given two strings <b><i>s</i></b> and <b><i>t</i></b> which consist of only lowercase letters.</p>

<p>String <b><i>t</i></b> is generated by random shuffling string <b><i>s</i></b> and then add one more letter at a random position.</p>

<p>Find the letter that was added in <b><i>t</i></b>.</p>

<p><b>Example:</b>
<pre>
Input:
s = "abcd"
t = "abcde"

Output:
e

Explanation:
'e' is the letter that was added.
</pre> instead-->
<p>给定两个字符串 <em><strong>s</strong></em> 和 <em><strong>t</strong></em>，它们只包含小写字母。</p>

<p>字符串&nbsp;<strong><em>t</em></strong>&nbsp;由字符串&nbsp;<strong><em>s</em></strong>&nbsp;随机重排，然后在随机位置添加一个字母。</p>

<p>请找出在 <em><strong>t</strong></em> 中被添加的字母。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre>输入：
s = &quot;abcd&quot;
t = &quot;abcde&quot;

输出：
e

解释：
&#39;e&#39; 是那个被添加的字母。
</pre>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def findTheDifference(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        res = 0
        for c in s+t:
            res ^= ord(c)
        return chr(res)
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-the-difference/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-difference/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-the-difference/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-the-difference/)