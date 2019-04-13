# 216. Combination Sum III | 组合总和 III

## Question description

<!--If you want to use the English description, use <div>
<p>Find all possible combinations of <i><b>k</b></i> numbers that add up to a number <i><b>n</b></i>, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>All numbers will be positive integers.</li>
	<li>The solution set must not contain duplicate combinations.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <i><b>k</b></i> = 3, <i><b>n</b></i> = 7
<strong>Output:</strong> [[1,2,4]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <i><b>k</b></i> = 3, <i><b>n</b></i> = 9
<strong>Output:</strong> [[1,2,6], [1,3,5], [2,3,4]]
</pre>
</div> instead-->
<p>找出所有相加之和为&nbsp;<em><strong>n</strong> </em>的&nbsp;<strong><em>k&nbsp;</em></strong>个数的组合<strong><em>。</em></strong>组合中只允许含有 1 -&nbsp;9 的正整数，并且每种组合中不存在重复的数字。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>所有数字都是正整数。</li>
	<li>解集不能包含重复的组合。&nbsp;</li>
</ul>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <em><strong>k</strong></em> = 3, <em><strong>n</strong></em> = 7
<strong>输出:</strong> [[1,2,4]]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <em><strong>k</strong></em> = 3, <em><strong>n</strong></em> = 9
<strong>输出:</strong> [[1,2,6], [1,3,5], [2,3,4]]
</pre>




## Solution

Language: **python3**  /  Runtime: 72 ms

```python3
class Solution:
    def dfs(self, k, n, m, cur, res):
        if k == 0:
            if n == 0:
                res.append(cur)
        else:
            if n > 0:
                for i in range(m, 10):
                    cur.append(i)
                    self.dfs(k-1, n-i, i+1, cur[:], res)
                    cur.pop()

    def combinationSum3(self, k, n):
        """
        :type k: int
        :type n: int
        :rtype: List[List[int]]
        """
        cur = []
        res = []
        self.dfs(k, n, 1, cur, res)
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combination-sum-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum-iii/description/)

Solution: [LeetCode](https://leetcode.com/articles/combination-sum-iii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combination-sum-iii/)