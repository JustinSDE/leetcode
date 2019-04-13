# 345. Reverse Vowels of a String | 反转字符串中的元音字母

## Question description

<!--If you want to use the English description, use <p>Write a function that takes a string as input and reverse only the vowels of a string.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;hello&quot;</span>
<strong>Output: </strong><span id="example-output-1">&quot;holle&quot;</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;leetcode&quot;</span>
<strong>Output: </strong><span id="example-output-2">&quot;leotcede&quot;</span></pre>
</div>

<p><b>Note:</b><br />
The vowels does not include the letter &quot;y&quot;.</p>

<p>&nbsp;</p>
 instead-->
<p>编写一个函数，以字符串作为输入，反转该字符串中的元音字母。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>&quot;hello&quot;
<strong>输出: </strong>&quot;holle&quot;
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>&quot;leetcode&quot;
<strong>输出: </strong>&quot;leotcede&quot;</pre>

<p><strong>说明:</strong><br>
元音字母不包含字母&quot;y&quot;。</p>


## Note

将字符串转为字符数组：`list(s)`，不必`[c for c in s]`


## Solution

Language: **python3**  /  Runtime: 96 ms

```python3
class Solution:
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        ss = [c for c in s]
        tmp = []
        for i, c in enumerate(ss):
            if c.lower() in 'aeiou':
                tmp.append((i, c))
        for ii, (i, c) in enumerate(tmp):
            ss[i] = tmp[-1 * ii -1][1]
        return ''.join(ss)

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-vowels-of-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-vowels-of-a-string/)