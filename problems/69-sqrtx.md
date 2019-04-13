# 69. Sqrt(x) | x 的平方根

## Question description

<!--If you want to use the English description, use <p>Implement <code>int sqrt(int x)</code>.</p>

<p>Compute and return the square root of <em>x</em>, where&nbsp;<em>x</em>&nbsp;is guaranteed to be a non-negative integer.</p>

<p>Since the return type&nbsp;is an integer, the decimal digits are truncated and only the integer part of the result&nbsp;is returned.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 4
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 8
<strong>Output:</strong> 2
<strong>Explanation:</strong> The square root of 8 is 2.82842..., and since 
&nbsp;            the decimal part is truncated, 2 is returned.
</pre>
 instead-->
<p>实现&nbsp;<code>int sqrt(int x)</code>&nbsp;函数。</p>

<p>计算并返回&nbsp;<em>x</em>&nbsp;的平方根，其中&nbsp;<em>x </em>是非负整数。</p>

<p>由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 4
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 8
<strong>输出:</strong> 2
<strong>说明:</strong> 8 的平方根是 2.82842..., 
&nbsp;    由于返回类型是整数，小数部分将被舍去。
</pre>


## Note

牛顿法求f(x)=0的根：

x = x - f(x)/f'(x)

对于sqrt(n)，也就是求f(x)=x^2-n=0的根。




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int mySqrt(int x) {
        int l = 0;
        int r = x;
        while (l < r) {
            int mid = (int)(l + r + 1l) >> 1;
            if (mid <= x / mid) l = mid;
            else r = mid - 1;
        }
        return l;
    }
}
```

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int mySqrt(int x) {
        // sqrt(x) = y  ->  x = y^2
        int left = 0;
        int right = x;
        while (left < right) {
            int mid = left + (right - left + 1ll) / 2;
            if (mid > x / mid) right = mid - 1;
            else left = mid;
        }
        return left;
    }
};
```

Language: **python3**  /  Runtime: 56 ms

```python3
class Solution:
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        pre = 1
        while True:
            res = 0.5 * (pre + x / pre)
            if abs(res - pre) < 1:
                break
            pre = res
        return int(res)

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sqrtx/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sqrtx/description/)

Solution: [LeetCode](https://leetcode.com/articles/sqrtx/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sqrtx/)