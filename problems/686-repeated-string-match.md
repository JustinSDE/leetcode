# 686. Repeated String Match | 重复叠加字符串匹配

## Question description

<!--If you want to use the English description, use <p>Given two strings A and B, find the minimum number of times A has to be repeated such that B is a substring of it. If no such solution, return -1.</p>

<p>For example, with A = &quot;abcd&quot; and B = &quot;cdabcdab&quot;.</p>

<p>Return 3, because by repeating A three times (&ldquo;abcdabcdabcd&rdquo;), B is a substring of it; and B is not a substring of A repeated two times (&quot;abcdabcd&quot;).</p>

<p><b>Note:</b><br />
The length of <code>A</code> and <code>B</code> will be between 1 and 10000.</p>
 instead-->
<p>给定两个字符串 A 和 B, 寻找重复叠加字符串A的最小次数，使得字符串B成为叠加后的字符串A的子串，如果不存在则返回 -1。</p>

<p>举个例子，A = &quot;abcd&quot;，B = &quot;cdabcdab&quot;。</p>

<p>答案为 3，&nbsp;因为 A 重复叠加三遍后为&nbsp;&ldquo;abcdabcdabcd&rdquo;，此时 B 是其子串；A 重复叠加两遍后为&quot;abcdabcd&quot;，B 并不是其子串。</p>

<p><strong>注意:</strong></p>

<p>&nbsp;<code>A</code>&nbsp;与&nbsp;<code>B</code>&nbsp;字符串的长度在1和10000区间范围内。</p>




## Solution

Language: **python3**  /  Runtime: 360 ms

```python3
class Solution:
    def repeatedStringMatch(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: int
        """
        for i in range(1, len(B) // len(A) + 4):
            if B in A*i:
                return i
        return -1
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/repeated-string-match/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/repeated-string-match/description/)

Solution: [LeetCode](https://leetcode.com/articles/repeated-string-match/)  /  [LeetCode中国](https://leetcode-cn.com/articles/repeated-string-match/)