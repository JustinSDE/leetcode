# 172. Factorial Trailing Zeroes | 阶乘后的零

## Question description

<!--If you want to use the English description, use <p>Given an integer <i>n</i>, return the number of trailing zeroes in <i>n</i>!.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;3! = 6, no trailing zero.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 5
<strong>Output:</strong> 1
<strong>Explanation:</strong>&nbsp;5! = 120, one trailing zero.</pre>

<p><b>Note: </b>Your solution should be in logarithmic time complexity.</p>
 instead-->
<p>给定一个整数 <em>n</em>，返回 <em>n</em>! 结果尾数中零的数量。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> 0
<strong>解释:</strong>&nbsp;3! = 6, 尾数中没有零。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 5
<strong>输出:</strong> 1
<strong>解释:</strong>&nbsp;5! = 120, 尾数中有 1 个零.</pre>

<p><strong>说明: </strong>你算法的时间复杂度应为&nbsp;<em>O</em>(log&nbsp;<em>n</em>)<em>&nbsp;</em>。</p>


## Note

注意int的边界


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        int res = 0;
        for(long p = 5; n / p > 0; p *= 5)
            res += n / p;
        return res;
    }
};
```

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def trailingZeroes(self, n):
        """
        :type n: int
        :rtype: int
        """
        p = 5
        res = 0
        while p <= n:
            res += n // p
            p *= 5
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/factorial-trailing-zeroes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/factorial-trailing-zeroes/description/)

Solution: [LeetCode](https://leetcode.com/articles/factorial-trailing-zeroes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/factorial-trailing-zeroes/)