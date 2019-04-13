# 119. Pascal's Triangle II | 杨辉三角 II

## Question description

<!--If you want to use the English description, use <p>Given a non-negative&nbsp;index <em>k</em>&nbsp;where <em>k</em> &le;&nbsp;33, return the <em>k</em><sup>th</sup>&nbsp;index row of the Pascal&#39;s triangle.</p>

<p>Note that the row index starts from&nbsp;0.</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" /><br />
<small>In Pascal&#39;s triangle, each number is the sum of the two numbers directly above it.</small></p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong> [1,3,3,1]
</pre>

<p><strong>Follow up:</strong></p>

<p>Could you optimize your algorithm to use only <em>O</em>(<em>k</em>) extra space?</p>
 instead-->
<p>给定一个非负索引&nbsp;<em>k</em>，其中 <em>k</em>&nbsp;&le;&nbsp;33，返回杨辉三角的第 <em>k </em>行。</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif"></p>

<p><small>在杨辉三角中，每个数是它左上方和右上方的数的和。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> [1,3,3,1]
</pre>

<p><strong>进阶：</strong></p>

<p>你可以优化你的算法到 <em>O</em>(<em>k</em>) 空间复杂度吗？</p>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        res = [1]
        for i in range(1, rowIndex+1):
            res.append(res[i-1] * (rowIndex-i+1)//i)
        return res

        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pascals-triangle-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pascals-triangle-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/pascals-triangle-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pascals-triangle-ii/)