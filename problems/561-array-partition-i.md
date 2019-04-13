# 561. Array Partition I | 数组拆分 I

## Question description

<!--If you want to use the English description, use <p>
Given an array of <b>2n</b> integers, your task is to group these integers into <b>n</b> pairs of integer, say (a<sub>1</sub>, b<sub>1</sub>), (a<sub>2</sub>, b<sub>2</sub>), ..., (a<sub>n</sub>, b<sub>n</sub>) which makes sum of min(a<sub>i</sub>, b<sub>i</sub>) for all i from 1 to n as large as possible.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [1,4,3,2]

<b>Output:</b> 4
<b>Explanation:</b> n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li><b>n</b> is a positive integer, which is in the range of [1, 10000].</li>
<li>All the integers in the array will be in the range of [-10000, 10000].</li>
</ol>
</p> instead-->
<p>给定长度为&nbsp;<strong>2n&nbsp;</strong>的数组, 你的任务是将这些数分成&nbsp;<strong>n </strong>对, 例如 (a<sub>1</sub>, b<sub>1</sub>), (a<sub>2</sub>, b<sub>2</sub>), ..., (a<sub>n</sub>, b<sub>n</sub>) ，使得从1 到&nbsp;n 的 min(a<sub>i</sub>, b<sub>i</sub>) 总和最大。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,4,3,2]

<strong>输出:</strong> 4
<strong>解释:</strong> n 等于 2, 最大总和为 4 = min(1, 2) + min(3, 4).
</pre>

<p><strong>提示:</strong></p>

<ol>
	<li><strong>n</strong>&nbsp;是正整数,范围在 [1, 10000].</li>
	<li>数组中的元素范围在 [-10000, 10000].</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 192 ms

```python3
class Solution:
    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(sorted(nums)[::2])
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/array-partition-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/array-partition-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/array-partition-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/array-partition-i/)