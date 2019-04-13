# 66. Plus One | 加一

## Question description

<!--If you want to use the English description, use <p>Given a <strong>non-empty</strong> array of digits&nbsp;representing a non-negative integer, plus one to the integer.</p>

<p>The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.</p>

<p>You may assume the integer does not contain any leading zero, except the number 0 itself.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3]
<strong>Output:</strong> [1,2,4]
<strong>Explanation:</strong> The array represents the integer 123.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,3,2,1]
<strong>Output:</strong> [4,3,2,2]
<strong>Explanation:</strong> The array represents the integer 4321.
</pre> instead-->
<p>给定一个由<strong>整数</strong>组成的<strong>非空</strong>数组所表示的非负整数，在该数的基础上加一。</p>

<p>最高位数字存放在数组的首位， 数组中每个元素只存储一个数字。</p>

<p>你可以假设除了整数 0 之外，这个整数不会以零开头。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
<strong>输出:</strong> [1,2,4]
<strong>解释:</strong> 输入数组表示数字 123。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [4,3,2,1]
<strong>输出:</strong> [4,3,2,2]
<strong>解释:</strong> 输入数组表示数字 4321。
</pre>




## Solution

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        res = list(digits)
        res[-1] += 1
        for i in range(len(res)-1, -1, -1):
            a, b = res[i] // 10, res[i] % 10
            res[i] = b
            if a == 0:
                break
            else:
                if i == 0:
                    res.insert(0, a)
                else:
                    res[i-1] += a
        return res
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/plus-one/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/plus-one/description/)

Solution: [LeetCode](https://leetcode.com/articles/plus-one/)  /  [LeetCode中国](https://leetcode-cn.com/articles/plus-one/)