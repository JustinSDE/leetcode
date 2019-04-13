# 70. Climbing Stairs | 爬楼梯

## Question description

<!--If you want to use the English description, use <p>You are climbing a stair case. It takes <em>n</em> steps to reach to the top.</p>

<p>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?</p>

<p><strong>Note:</strong> Given <em>n</em> will be a positive integer.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
</pre>
 instead-->
<p>假设你正在爬楼梯。需要 <em>n</em>&nbsp;阶你才能到达楼顶。</p>

<p>每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？</p>

<p><strong>注意：</strong>给定 <em>n</em> 是一个正整数。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong> 2
<strong>输出：</strong> 2
<strong>解释：</strong> 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong> 3
<strong>输出：</strong> 3
<strong>解释：</strong> 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
</pre>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        steps = [1, 2]
        if n < 3:
            return n
        else:
            for i in range(n-2):
                if i % 2 == 0:
                    steps[0] += steps[1]
                else:
                    steps[1] += steps[0]
            if n % 2 == 0:
                return steps[1]
            else:
                return steps[0]
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/climbing-stairs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/climbing-stairs/description/)

Solution: [LeetCode](https://leetcode.com/articles/climbing-stairs/)  /  [LeetCode中国](https://leetcode-cn.com/articles/climbing-stairs/)