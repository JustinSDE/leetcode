# 1020. Number of Enclaves | 飞地的数量

## Question description

<!--If you want to use the English description, use <p>Given a 2D array <code>A</code>, each cell is 0 (representing sea) or 1 (representing land)</p>

<p>A move consists of walking from one land square 4-directionally to another land square, or off the boundary of the grid.</p>

<p>Return the number of land squares in the grid for which we <strong>cannot</strong> walk off the boundary of the grid in any number of moves.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]</span>
<strong>Output: </strong><span id="example-output-1">3</span>
<strong>Explanation: </strong>
There are three 1s that are enclosed by 0s, and one 1 that isn&#39;t enclosed because its on the boundary.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[[0,1,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,0]]</span>
<strong>Output: </strong><span id="example-output-2">0</span>
<strong>Explanation: </strong>
All 1s are either on the boundary or can reach the boundary.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 500</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 500</code></li>
	<li><code>0 &lt;= A[i][j] &lt;= 1</code></li>
	<li>All rows have the same size.</li>
</ol> instead-->
<p>给出一个二维数组&nbsp;<code>A</code>，每个单元格为 0（代表海）或 1（代表陆地）。</p>

<p>移动是指在陆地上从一个地方走到另一个地方（朝四个方向之一）或离开网格的边界。</p>

<p>返回网格中<strong>无法</strong>在任意次数的移动中离开网格边界的陆地单元格的数量。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]
<strong>输出：</strong>3
<strong>解释： </strong>
有三个 1 被 0 包围。一个 1 没有被包围，因为它在边界上。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[0,1,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,0]]
<strong>输出：</strong>0
<strong>解释：</strong>
所有 1 都在边界上或可以到达边界。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 500</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 500</code></li>
	<li><code>0 &lt;= A[i][j] &lt;= 1</code></li>
	<li>所有行的大小都相同</li>
</ol>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    int[] dx = new int[] {-1, 0, 1, 0};
    int[] dy = new int[] {0, 1, 0, -1};
    int m, n;

    private void dfs(int[][] A, int i, int j) {
        A[i][j] = 0;
        for (int k = 0; k < 4; k++) {
            int x = i + dx[k];
            int y = j + dy[k];
            if (0 <= x && x < m && 0 <= y && y < n && A[x][y] == 1) dfs(A, x, y);
        }
    }

    public int numEnclaves(int[][] A) {
        m = A.length;
        if (m == 0) return 0;
        n = A[0].length;
        if (n == 0) return 0;
        
        for (int i = 0; i < m; i++) {
            if (A[i][0] == 1) dfs(A, i, 0);
            if (A[i][n - 1] == 1) dfs(A, i, n - 1);
        }
        for (int i = 0; i < n; i++) {
            if (A[0][i] == 1) dfs(A, 0, i);
            if (A[m - 1][i] == 1) dfs(A, m - 1, i);
        }
        int res = 0;
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                res += A[i][j];
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-enclaves/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-enclaves/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-enclaves/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-enclaves/)