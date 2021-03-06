# 405. Convert a Number to Hexadecimal | 数字转换为十六进制数

## Question description

<!--If you want to use the English description, use <p>
Given an integer, write an algorithm to convert it to hexadecimal. For negative integer, <a href="https://en.wikipedia.org/wiki/Two%27s_complement" target="_blank">two’s complement</a> method is used.
</p>

<p><b>Note:</b>
<ol>
<li>All letters in hexadecimal (<code>a-f</code>) must be in lowercase.</li>
<li>The hexadecimal string must not contain extra leading <code>0</code>s. If the number is zero, it is represented by a single zero character <code>'0'</code>; otherwise, the first character in the hexadecimal string will not be the zero character.</li>
<li>The given number is guaranteed to fit within the range of a 32-bit signed integer.</li>
<li>You <b>must not use <i>any</i> method provided by the library</b> which converts/formats the number to hex directly.</li>
</ol>
</p>

<p><b>Example 1:</b>
<pre>
Input:
26

Output:
"1a"
</pre>
</p>

<p><b>Example 2:</b>
<pre>
Input:
-1

Output:
"ffffffff"
</pre>
</p> instead-->
<p>给定一个整数，编写一个算法将这个数转换为十六进制数。对于负整数，我们通常使用&nbsp;<a href="https://baike.baidu.com/item/%E8%A1%A5%E7%A0%81/6854613?fr=aladdin">补码运算</a>&nbsp;方法。</p>

<p><strong>注意:</strong></p>

<ol>
	<li>十六进制中所有字母(<code>a-f</code>)都必须是小写。</li>
	<li>十六进制字符串中不能包含多余的前导零。如果要转化的数为0，那么以单个字符<code>&#39;0&#39;</code>来表示；对于其他情况，十六进制字符串中的第一个字符将不会是0字符。&nbsp;</li>
	<li>给定的数确保在32位有符号整数范围内。</li>
	<li><strong>不能使用任何由库提供的将数字直接转换或格式化为十六进制的方法。</strong></li>
</ol>

<p><strong>示例 1：</strong></p>

<pre>
输入:
26

输出:
&quot;1a&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre>
输入:
-1

输出:
&quot;ffffffff&quot;
</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public String toHex(int num) {
        if (num == 0) return "0";
        long n = (long)num;
        StringBuilder sb = new StringBuilder();
        String s = "0123456789abcdef";
        n = n < 0 ? 4294967296l + n : n;
        while (n > 0) {
            sb.append(s.charAt((int)(n % 16)));
            n /= 16;
        }
        return sb.reverse().toString();
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/convert-a-number-to-hexadecimal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/convert-a-number-to-hexadecimal/description/)

Solution: [LeetCode](https://leetcode.com/articles/convert-a-number-to-hexadecimal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/convert-a-number-to-hexadecimal/)