# 628. Maximum Product of Three Numbers | 三个数的最大乘积

## Question description

<!--If you want to use the English description, use <p>Given an integer array, find three numbers whose product is maximum and output the maximum product.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [1,2,3]
<b>Output:</b> 6
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [1,2,3,4]
<b>Output:</b> 24
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The length of the given array will be in range [3,10<sup>4</sup>] and all elements are in the range [-1000, 1000].</li>
	<li>Multiplication of any three numbers in the input won&#39;t exceed the range of 32-bit signed integer.</li>
</ol>

<p>&nbsp;</p>
 instead-->
<p>给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3]
<strong>输出:</strong> 6
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4]
<strong>输出:</strong> 24
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>给定的整型数组长度范围是[3,10<sup>4</sup>]，数组中所有的元素范围是[-1000, 1000]。</li>
	<li>输入的数组中任意三个数的乘积不会超出32位有符号整数的范围。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int maximumProduct(int[] nums) {
        int m1 = Integer.MIN_VALUE, m2 = Integer.MIN_VALUE, m3 = Integer.MIN_VALUE, m4 = 0, m5 = 0;
        for (int a : nums) {
            if (a > m3) {
                if (a > m2) {
                    if (a > m1) {
                        m3 = m2;
                        m2 = m1;
                        m1 = a;
                    } else {
                        m3 = m2;
                        m2 = a;
                    }
                } else {
                    m3 = a;
                }
            }
            if (a < 0) {
                if (a < m5) {
                    if (a < m4) {
                        m5 = m4;
                        m4 = a;
                    } else {
                        m5 = a;
                    }
                }
            }
        }
        return Math.max(m1 * m2 * m3, m4 * m5 * m1);
    }
}
```

Language: **python3**  /  Runtime: 100 ms

```python3
import heapq

class Solution:
    def maximumProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        a = heapq.nlargest(3, nums)
        b = heapq.nsmallest(3, nums)
        return max(a[0] * a[1] * a[2], a[0] * b[0] * b[1])              
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-of-three-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-of-three-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-of-three-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-of-three-numbers/)