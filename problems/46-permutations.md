# 46. Permutations | 全排列

## Question description

<!--If you want to use the English description, use <p>Given a collection of <strong>distinct</strong> integers, return all possible permutations.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3]
<strong>Output:</strong>
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
</pre>
 instead-->
<p>给定一个<strong>没有重复</strong>数字的序列，返回其所有可能的全排列。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
<strong>输出:</strong>
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]</pre>


## Note

用Python的话，可以直接用内建的`itertools`模块，一行搞定，宛如开挂。


## Solution

Language: **python3**  /  Runtime: 76 ms

```python3
class Solution:
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        return list(itertools.permutations(nums))
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/permutations/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/permutations/description/)

Solution: [LeetCode](https://leetcode.com/articles/permutations/)  /  [LeetCode中国](https://leetcode-cn.com/articles/permutations/)