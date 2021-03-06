# 200. Number of Islands | 岛屿的个数

## Question description

<!--If you want to use the English description, use <p>Given a 2d grid map of <code>&#39;1&#39;</code>s (land) and <code>&#39;0&#39;</code>s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.</p>

<p><b>Example 1:</b></p>

<pre>
<strong>Input:</strong>
11110
11010
11000
00000

<strong>Output:</strong>&nbsp;1
</pre>

<p><b>Example 2:</b></p>

<pre>
<strong>Input:</strong>
11000
11000
00100
00011

<strong>Output: </strong>3
</pre> instead-->
<p>给定一个由&nbsp;<code>&#39;1&#39;</code>（陆地）和 <code>&#39;0&#39;</code>（水）组成的的二维网格，计算岛屿的数量。一个岛被水包围，并且它是通过水平方向或垂直方向上相邻的陆地连接而成的。你可以假设网格的四个边均被水包围。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
11110
11010
11000
00000

<strong>输出:</strong>&nbsp;1
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>
11000
11000
00100
00011

<strong>输出: </strong>3
</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    void dfs(vector<vector<char>>& grid, int r, int c, int n, int m) {
        if (grid[r][c] != '1') {
            return;
        }
        grid[r][c] = '2';
        int dx[] = {-1, 0, 1, 0};
        int dy[] = {0, 1, 0, -1};
        for (int i=0; i<4; ++i) {
            int nr = r + dx[i];
            int nc = c + dy[i];
            if (nr >= 0 && nr < n && nc >= 0 && nc < m && grid[nr][nc] == '1') {
                dfs(grid, nr, nc, n, m);
            }
        }
    }

    int numIslands(vector<vector<char>>& grid) {
        if (!grid.size() || !grid[0].size()) return 0;
        int res = 0;
        int n = grid.size();
        int m = grid[0].size();
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                if (grid[i][j] == '1') {
                    res++;
                    dfs(grid, i, j, n, m);
                }
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-islands/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-islands/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-islands/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-islands/)