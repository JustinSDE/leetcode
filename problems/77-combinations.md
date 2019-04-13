# 77. Combinations | 组合

## Question description

<!--If you want to use the English description, use <p>Given two integers <em>n</em> and <em>k</em>, return all possible combinations of <em>k</em> numbers out of 1 ... <em>n</em>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;n = 4, k = 2
<strong>Output:</strong>
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
</pre>
 instead-->
<p>给定两个整数 <em>n</em> 和 <em>k</em>，返回 1 ... <em>n </em>中所有可能的 <em>k</em> 个数的组合。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;n = 4, k = 2
<strong>输出:</strong>
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]</pre>




## Solution

Language: **python3**  /  Runtime: 196 ms

```python3
class Solution:
    def combine(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[List[int]]
        """
        return list(itertools.combinations(range(1, n+1), k))
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combinations/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combinations/description/)

Solution: [LeetCode](https://leetcode.com/articles/combinations/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combinations/)