# 47. Permutations II | 全排列 II

## Question description

<!--If you want to use the English description, use <p>Given a collection of numbers that might contain duplicates, return all possible unique permutations.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,1,2]
<strong>Output:</strong>
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
</pre>
 instead-->
<p>给定一个可包含重复数字的序列，返回所有不重复的全排列。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,1,2]
<strong>输出:</strong>
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]</pre>


## Note

这个如果用Python自带的`itertools.permutations`就会有重复，所以，还是要会自己实现。简单的做法就是递归，难点主要在于不重复。思路是：先排序，然后根据上一个组合来判断是否重复。递归注意递归出口条件。


## Solution

Language: **python3**  /  Runtime: 88 ms

```python3
class Solution:
    def permuteUnique(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        if len(nums) == 0:
            return []
        if len(nums) == 1:
            return [nums]
        nums.sort()
        res = []
        for i, num in enumerate(nums):
            if not res or res[-1][0] != num:
                for r in self.permuteUnique(nums[:i] + nums[i+1:]):
                    res.append([num, *r])
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/permutations-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/permutations-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/permutations-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/permutations-ii/)