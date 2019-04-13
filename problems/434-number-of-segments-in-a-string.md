# 434. Number of Segments in a String | 字符串中的单词数

## Question description

<!--If you want to use the English description, use <p>Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.</p>

<p>Please note that the string does not contain any <b>non-printable</b> characters.</p>

<p><b>Example:</b></p>
<pre>
<b>Input:</b> "Hello, my name is John"
<b>Output:</b> 5
</pre>
</p> instead-->
<p>统计字符串中的单词个数，这里的单词指的是连续的不是空格的字符。</p>

<p>请注意，你可以假定字符串里不包括任何不可打印的字符。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;Hello, my name is John&quot;
<strong>输出:</strong> 5
</pre>




## Solution

Language: **python3**  /  Runtime: 32 ms

```python3
class Solution:
    def countSegments(self, s):
        """
        :type s: str
        :rtype: int
        """
        return len(s.split())
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-segments-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-segments-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-segments-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-segments-in-a-string/)