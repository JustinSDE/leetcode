# 892. Surface Area of 3D Shapes | 三维形体的表面积

## Question description

<!--If you want to use the English description, use <p>On a&nbsp;<code>N&nbsp;*&nbsp;N</code>&nbsp;grid, we place some&nbsp;<code>1 * 1 * 1&nbsp;</code>cubes.</p>

<p>Each value&nbsp;<code>v = grid[i][j]</code>&nbsp;represents a tower of&nbsp;<code>v</code>&nbsp;cubes placed on top of grid cell&nbsp;<code>(i, j)</code>.</p>

<p>Return the total surface area of the resulting shapes.</p>

<p>&nbsp;</p>

<div>
<div>
<div>
<ul>
</ul>
</div>
</div>
</div>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[[2]]</span>
<strong>Output: </strong><span id="example-output-1">10</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[[1,2],[3,4]]</span>
<strong>Output: </strong><span id="example-output-2">34</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">[[1,0],[0,2]]</span>
<strong>Output: </strong><span id="example-output-3">16</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-4-1">[[1,1,1],[1,0,1],[1,1,1]]</span>
<strong>Output: </strong><span id="example-output-4">32</span>
</pre>

<div>
<p><strong>Example 5:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-5-1">[[2,2,2],[2,1,2],[2,2,2]]</span>
<strong>Output: </strong><span id="example-output-5">46</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 50</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 50</code></li>
</ul>
</div>
</div>
</div>
</div>
</div>
 instead-->
<p>在&nbsp;<code>N&nbsp;*&nbsp;N</code>&nbsp;的网格上，我们放置一些&nbsp;<code>1 * 1 * 1&nbsp;</code>&nbsp;的立方体。</p>

<p>每个值&nbsp;<code>v = grid[i][j]</code>&nbsp;表示&nbsp;<code>v</code>&nbsp;个正方体叠放在单元格&nbsp;<code>(i, j)</code>&nbsp;上。</p>

<p>返回结果形体的总表面积。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[2]]
<strong>输出：</strong>10
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[1,2],[3,4]]
<strong>输出：</strong>34
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[[1,0],[0,2]]
<strong>输出：</strong>16
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[[1,1,1],[1,0,1],[1,1,1]]
<strong>输出：</strong>32
</pre>

<p><strong>示例&nbsp;5：</strong></p>

<pre><strong>输入：</strong>[[2,2,2],[2,1,2],[2,2,2]]
<strong>输出：</strong>46
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 50</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 50</code></li>
</ul>


## Note

题目与[883. Projection Area of 3D Shapes](https://leetcode.com/problems/projection-area-of-3d-shapes/description/)很接近，很容易让人往投影方向想，其实并不是利用投影求表面积，因为投影会漏掉凹处的表面积。思路就是：最前和最后块的高度（如果是同一块，这个要加两次）+中间块的相邻高度差。


## Solution

Language: **python3**  /  Runtime: 92 ms

```python3
class Solution:
    def surfaceArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        res = 0
        for g in grid + list(zip(*grid)):
            res += len(g) - g.count(0)
            for i, s in enumerate(g):
                if i == 0 or i == len(g) - 1:
                    res += s * (1 + int(len(g) == 1))
                if i > 0:
                    res += abs(g[i] - g[i-1])
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/surface-area-of-3d-shapes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/surface-area-of-3d-shapes/description/)

Solution: [LeetCode](https://leetcode.com/articles/surface-area-of-3d-shapes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/surface-area-of-3d-shapes/)