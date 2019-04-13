# 130. Surrounded Regions | 被围绕的区域

## Question description

<!--If you want to use the English description, use <p>Given a 2D board containing <code>&#39;X&#39;</code> and <code>&#39;O&#39;</code> (<strong>the letter O</strong>), capture all regions surrounded by <code>&#39;X&#39;</code>.</p>

<p>A region is captured by flipping all <code>&#39;O&#39;</code>s into <code>&#39;X&#39;</code>s in that surrounded region.</p>

<p><strong>Example:</strong></p>

<pre>
X X X X
X O O X
X X O X
X O X X
</pre>

<p>After running your function, the board should be:</p>

<pre>
X X X X
X X X X
X X X X
X O X X
</pre>

<p><strong>Explanation:</strong></p>

<p>Surrounded regions shouldn&rsquo;t be on the border, which means that any <code>&#39;O&#39;</code>&nbsp;on the border of the board are not flipped to <code>&#39;X&#39;</code>. Any <code>&#39;O&#39;</code>&nbsp;that is not on the border and it is not connected to an <code>&#39;O&#39;</code>&nbsp;on the border will be flipped to <code>&#39;X&#39;</code>. Two cells are connected if they are adjacent cells connected horizontally or vertically.</p>
 instead-->
<p>给定一个二维的矩阵，包含&nbsp;<code>&#39;X&#39;</code>&nbsp;和&nbsp;<code>&#39;O&#39;</code>（<strong>字母 O</strong>）。</p>

<p>找到所有被 <code>&#39;X&#39;</code> 围绕的区域，并将这些区域里所有的&nbsp;<code>&#39;O&#39;</code> 用 <code>&#39;X&#39;</code> 填充。</p>

<p><strong>示例:</strong></p>

<pre>X X X X
X O O X
X X O X
X O X X
</pre>

<p>运行你的函数后，矩阵变为：</p>

<pre>X X X X
X X X X
X X X X
X O X X
</pre>

<p><strong>解释:</strong></p>

<p>被围绕的区间不会存在于边界上，换句话说，任何边界上的&nbsp;<code>&#39;O&#39;</code>&nbsp;都不会被填充为&nbsp;<code>&#39;X&#39;</code>。 任何不在边界上，或不与边界上的&nbsp;<code>&#39;O&#39;</code>&nbsp;相连的&nbsp;<code>&#39;O&#39;</code>&nbsp;最终都会被填充为&nbsp;<code>&#39;X&#39;</code>。如果两个元素在水平或垂直方向相邻，则称它们是&ldquo;相连&rdquo;的。</p>




## Solution

Language: **cpp**  /  Runtime: 24 ms

```cpp
class Solution {
public:
    void solve(vector<vector<char>>& board) {
        if (!board.size() || !board[0].size()) return;
        int n = board.size();
        int m = board[0].size();
        vector<vector<int> > A = vector<vector<int> >(n, vector<int>(m, 0));
        set<pair<int, int> > P;
        for (int i=0; i<m; ++i) {
            if (board[0][i] == 'O') {
                A[0][i] = 1;
                P.insert(make_pair(0, i));
            }
        } 
        for (int i=0; i<n; ++i) {
            if (board[i][m-1] == 'O') {
                A[i][m-1] = 1;
                P.insert(make_pair(i, m-1));
            }
        }
        for (int i=0; i<m; ++i) {
            if (board[n-1][i] == 'O') {
                A[n-1][i] = 1;
                P.insert(make_pair(n-1, i));
            }
        }
        for (int i=0; i<n; ++i) {
            if (board[i][0] == 'O') {
                A[i][0] = 1;
                P.insert(make_pair(i, 0));
            }
        }

        queue<pair<int, int> > Q;
        for (auto p : P) {
            // cout << "(" << p.first << ", " << p.second << ")" << endl;
            Q.push(p);
        }
        int dx[] = {0, 1, 0, -1};
        int dy[] = {1, 0, -1, 0};
        while (!Q.empty()) {
            auto p = Q.front();
            Q.pop();
            for (int i=0; i<4; ++i) {
                int nx = p.first + dx[i];
                int ny = p.second + dy[i];
                if (nx >= 0 && nx < n && ny >= 0 && ny < m && board[nx][ny] == 'O' && A[nx][ny] == 0) {
                    Q.push(make_pair(nx, ny));
                    A[nx][ny] = 1;
                }
            }
        }

        for (int i=0; i<n; ++i) 
            for (int j=0; j<m; ++j) 
                if (A[i][j] == 0) 
                    board[i][j] = 'X';
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/surrounded-regions/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/surrounded-regions/description/)

Solution: [LeetCode](https://leetcode.com/articles/surrounded-regions/)  /  [LeetCode中国](https://leetcode-cn.com/articles/surrounded-regions/)