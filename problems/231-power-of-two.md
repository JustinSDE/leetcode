# 231. Power of Two | 2的幂

## Question description

<!--If you want to use the English description, use <p>Given an integer, write a function to determine if it is a power of two.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1
<strong>Output:</strong> true 
<strong>Explanation: </strong>2<sup>0</sup>&nbsp;= 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 16
<strong>Output:</strong> true
<strong>Explanation: </strong>2<sup>4</sup>&nbsp;= 16</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 218
<strong>Output:</strong> false</pre>
 instead-->
<p>给定一个整数，编写一个函数来判断它是否是 2 的幂次方。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1
<strong>输出:</strong> true
<strong>解释: </strong>2<sup>0</sup>&nbsp;= 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 16
<strong>输出:</strong> true
<strong>解释: </strong>2<sup>4</sup>&nbsp;= 16</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> 218
<strong>输出:</strong> false</pre>


## Note

利用位运算来判断是否为2的幂。2的幂的二进制特点是：最高位为1，其余全为0;而2的幂-1的二进制特点是：所有位都为1。因此，进行按位与，结果是0。


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n > 0)
            return !(n & (n-1));
        else
            return false;
    }
};
```

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        return not (n & (n-1)) if n > 0 else False
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/power-of-two/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/power-of-two/description/)

Solution: [LeetCode](https://leetcode.com/articles/power-of-two/)  /  [LeetCode中国](https://leetcode-cn.com/articles/power-of-two/)