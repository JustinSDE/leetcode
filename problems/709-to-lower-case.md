# 709. To Lower Case | 转换成小写字母

## Question description

<!--If you want to use the English description, use <p>Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;Hello&quot;</span>
<strong>Output: </strong><span id="example-output-1">&quot;hello&quot;</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;here&quot;</span>
<strong>Output: </strong><span id="example-output-2">&quot;here&quot;</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;LOVELY&quot;</span>
<strong>Output: </strong><span id="example-output-3">&quot;lovely&quot;</span>
</pre>
</div>
</div>
</div>
 instead-->
<p>实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>&quot;Hello&quot;
<strong>输出: </strong>&quot;hello&quot;</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入: </strong>&quot;here&quot;
<strong>输出: </strong>&quot;here&quot;</pre>

<p><strong>示例</strong><strong>&nbsp;3：</strong></p>

<pre>
<strong>输入: </strong>&quot;LOVELY&quot;
<strong>输出: </strong>&quot;lovely&quot;
</pre>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def toLowerCase(self, str):
        """
        :type str: str
        :rtype: str
        """
        return str.lower()
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/to-lower-case/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/to-lower-case/description/)

Solution: [LeetCode](https://leetcode.com/articles/to-lower-case/)  /  [LeetCode中国](https://leetcode-cn.com/articles/to-lower-case/)