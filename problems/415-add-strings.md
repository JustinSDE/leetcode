# 415. Add Strings | 字符串相加

## Question description

<!--If you want to use the English description, use <p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as string, return the sum of <code>num1</code> and <code>num2</code>.</p>

<p><b>Note:</b>
<ol>
<li>The length of both <code>num1</code> and <code>num2</code> is < 5100.</li>
<li>Both <code>num1</code> and <code>num2</code> contains only digits <code>0-9</code>.</li>
<li>Both <code>num1</code> and <code>num2</code> does not contain any leading zero.</li>
<li>You <b>must not use any built-in BigInteger library</b> or <b>convert the inputs to integer</b> directly.</li>
</ol>
</p> instead-->
<p>给定两个字符串形式的非负整数&nbsp;<code>num1</code> 和<code>num2</code>&nbsp;，计算它们的和。</p>

<p><strong>注意：</strong></p>

<ol>
	<li><code>num1</code> 和<code>num2</code>&nbsp;的长度都小于 5100.</li>
	<li><code>num1</code> 和<code>num2</code> 都只包含数字&nbsp;<code>0-9</code>.</li>
	<li><code>num1</code> 和<code>num2</code> 都不包含任何前导零。</li>
	<li><strong>你不能使用任何內建 BigInteger 库，&nbsp;也不能直接将输入的字符串转换为整数形式。</strong></li>
</ol>


## Note

大数加法


## Solution

Language: **python3**  /  Runtime: 120 ms

```python3
class Solution:
    def addStrings(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        if not num1 and not num2:
            return ''
        tmp = []
        for i in range(max(len(num1), len(num2))):
            i1 = len(num1) - 1 - i
            i2 = len(num2) - 1 - i
            # Note: Python's list can use a negative index
            if 0 <= i1 < len(num1):
                x = int(num1[i1])
            else:
                x = 0
            if 0 <= i2 < len(num2):
                y = int(num2[i2])
            else:
                y = 0
            tmp.insert(0, x + y)
        i = len(tmp) - 1
        # Note: Every digit has to judge, can't meet <=9 then break
        while i >= 0:
            if tmp[i] > 9:
                a = tmp[i] // 10
                tmp[i] %= 10
                if i == 0:
                    tmp.insert(0, 0)
                    i += 1
                tmp[i-1] += a
            i -= 1
        return ''.join(map(str, tmp))
  
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-strings/)