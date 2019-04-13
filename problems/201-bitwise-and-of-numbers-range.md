# 201. Bitwise AND of Numbers Range | 数字范围按位与

## Question description

<!--If you want to use the English description, use <p>Given a range [m, n] where 0 &lt;= m &lt;= n &lt;= 2147483647, return the bitwise AND of all numbers in this range, inclusive.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [5,7]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [0,1]
<strong>Output:</strong> 0</pre> instead-->
<p>给定范围 [m, n]，其中 0 &lt;= m &lt;= n &lt;= 2147483647，返回此范围内所有数字的按位与（包含 m, n 两端点）。</p>

<p><strong>示例 1:&nbsp;</strong></p>

<pre><strong>输入:</strong> [5,7]
<strong>输出:</strong> 4</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [0,1]
<strong>输出:</strong> 0</pre>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        // n & (n - 1) 可以把最右的1变为0
        while (n > m) {
            n &= (n - 1);
        }
        return n;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/description/)

Solution: [LeetCode](https://leetcode.com/articles/bitwise-and-of-numbers-range/)  /  [LeetCode中国](https://leetcode-cn.com/articles/bitwise-and-of-numbers-range/)