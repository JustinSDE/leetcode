# 118. Pascal's Triangle | 杨辉三角

## Question description

<!--If you want to use the English description, use <p>Given a non-negative integer&nbsp;<em>numRows</em>, generate the first <em>numRows</em> of Pascal&#39;s triangle.</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" style="height:240px; width:260px" /><br />
<small>In Pascal&#39;s triangle, each number is the sum of the two numbers directly above it.</small></p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 5
<strong>Output:</strong>
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
</pre>
 instead-->
<p>给定一个非负整数&nbsp;<em>numRows，</em>生成杨辉三角的前&nbsp;<em>numRows&nbsp;</em>行。</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif"></p>

<p><small>在杨辉三角中，每个数是它左上方和右上方的数的和。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 5
<strong>输出:</strong>
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]</pre>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = []
        if numRows == 0:
            return res
        res.append([1])
        if numRows == 1:
            return res
        for l in range(2, numRows+1):
            t = [None] * l
            t[0] = 1
            t[-1] = 1
            for i in range(1, len(t)-1):
                t[i] = res[-1][i] + res[-1][i-1]
            res.append(t)
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pascals-triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pascals-triangle/description/)

Solution: [LeetCode](https://leetcode.com/articles/pascals-triangle/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pascals-triangle/)