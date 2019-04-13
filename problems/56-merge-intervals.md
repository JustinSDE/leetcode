# 56. Merge Intervals | 合并区间

## Question description

<!--If you want to use the English description, use <p>Given a collection of intervals, merge all overlapping intervals.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [[1,3],[2,6],[8,10],[15,18]]
<strong>Output:</strong> [[1,6],[8,10],[15,18]]
<strong>Explanation:</strong> Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [[1,4],[4,5]]
<strong>Output:</strong> [[1,5]]
<strong>Explanation:</strong> Intervals [1,4] and [4,5] are considered overlapping.</pre>
 instead-->
<p>给出一个区间的集合，请合并所有重叠的区间。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [[1,3],[2,6],[8,10],[15,18]]
<strong>输出:</strong> [[1,6],[8,10],[15,18]]
<strong>解释:</strong> 区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [[1,4],[4,5]]
<strong>输出:</strong> [[1,5]]
<strong>解释:</strong> 区间 [1,4] 和 [4,5] 可被视为重叠区间。</pre>


## Note

重叠包括三种情况：

1、相交。如：[1,3],[2,6]

2、相切。如：[1,4],[4,5]

3、包含。如：[1,5],[2,3]

先按起点进行升序排序，如果上一个的终点小于下一个的起点，那么就不合并，否则就合并。合并后新的终点是取两个终点的最大值。


## Solution

Language: **python3**  /  Runtime: 140 ms

```python3
# Definition for an interval.
# class Interval:
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution:
    def merge(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[Interval]
        """
        intervals.sort(key=lambda x: x.start)
        res = []
        for it in intervals:
            if not res or res[-1].end < it.start:
                res.append(it)
            else:
                res[-1].end = max(res[-1].end, it.end)
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-intervals/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-intervals/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-intervals/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-intervals/)