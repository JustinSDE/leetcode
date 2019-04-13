# 717. 1-bit and 2-bit Characters | 1比特与2比特字符

## Question description

<!--If you want to use the English description, use <p>We have two special characters. The first character can be represented by one bit <code>0</code>. The second character can be represented by two bits (<code>10</code> or <code>11</code>).  </p>

<p>Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> 
bits = [1, 0, 0]
<b>Output:</b> True
<b>Explanation:</b> 
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> 
bits = [1, 1, 1, 0]
<b>Output:</b> False
<b>Explanation:</b> 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.
</pre>
</p>

<p><b>Note:</b>
<li><code>1 <= len(bits) <= 1000</code>.</li>
<li><code>bits[i]</code> is always <code>0</code> or <code>1</code>.</li>
</p> instead-->
<p>有两种特殊字符。第一种字符可以用一比特<code>0</code>来表示。第二种字符可以用两比特(<code>10</code>&nbsp;或&nbsp;<code>11</code>)来表示。</p>

<p>现给一个由若干比特组成的字符串。问最后一个字符是否必定为一个一比特字符。给定的字符串总是由0结束。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> 
bits = [1, 0, 0]
<strong>输出:</strong> True
<strong>解释:</strong> 
唯一的编码方式是一个两比特字符和一个一比特字符。所以最后一个字符是一比特字符。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> 
bits = [1, 1, 1, 0]
<strong>输出:</strong> False
<strong>解释:</strong> 
唯一的编码方式是两比特字符和两比特字符。所以最后一个字符不是一比特字符。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>1 &lt;= len(bits) &lt;= 1000</code>.</li>
	<li><code>bits[i]</code> 总是<code>0</code> 或&nbsp;<code>1</code>.</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        i = 0
        while i < len(bits):
            if i == len(bits) - 1 and bits[i] == 0:
                return True
            if bits[i] == 1:
                i += 2
            else:
                i += 1
        return False
                
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/1-bit-and-2-bit-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters/description/)

Solution: [LeetCode](https://leetcode.com/articles/1-bit-and-2-bit-characters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/1-bit-and-2-bit-characters/)