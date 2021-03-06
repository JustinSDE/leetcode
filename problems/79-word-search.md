# 79. Word Search | 单词搜索

## Question description

<!--If you want to use the English description, use <p>Given a 2D board and a word, find if the word exists in the grid.</p>

<p>The word can be constructed from letters of sequentially adjacent cell, where &quot;adjacent&quot; cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.</p>

<p><strong>Example:</strong></p>

<pre>
board =
[
  [&#39;A&#39;,&#39;B&#39;,&#39;C&#39;,&#39;E&#39;],
  [&#39;S&#39;,&#39;F&#39;,&#39;C&#39;,&#39;S&#39;],
  [&#39;A&#39;,&#39;D&#39;,&#39;E&#39;,&#39;E&#39;]
]

Given word = &quot;<strong>ABCCED</strong>&quot;, return <strong>true</strong>.
Given word = &quot;<strong>SEE</strong>&quot;, return <strong>true</strong>.
Given word = &quot;<strong>ABCB</strong>&quot;, return <strong>false</strong>.
</pre>
 instead-->
<p>给定一个二维网格和一个单词，找出该单词是否存在于网格中。</p>

<p>单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中&ldquo;相邻&rdquo;单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。</p>

<p><strong>示例:</strong></p>

<pre>board =
[
  [&#39;A&#39;,&#39;B&#39;,&#39;C&#39;,&#39;E&#39;],
  [&#39;S&#39;,&#39;F&#39;,&#39;C&#39;,&#39;S&#39;],
  [&#39;A&#39;,&#39;D&#39;,&#39;E&#39;,&#39;E&#39;]
]

给定 word = &quot;<strong>ABCCED</strong>&quot;, 返回 <strong>true</strong>.
给定 word = &quot;<strong>SEE</strong>&quot;, 返回 <strong>true</strong>.
给定 word = &quot;<strong>ABCB</strong>&quot;, 返回 <strong>false</strong>.</pre>




## Solution

Language: **cpp**  /  Runtime: 20 ms

```cpp
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

const int N = 1000;

class Solution {
public:
    int n, m;
    bool vt[N][N];
    bool res;
    
    void dfs(vector<vector<char>>& board, string& word, int x, int y, int p) {
        if (p == word.size() || res) {
            res = true;
            return;
        }

        int dx[] = {1, 0, -1, 0};
        int dy[] = {0, 1, 0, -1};
        for (int i=0; i<4; ++i) {
            int nx = x + dx[i];
            int ny = y + dy[i];
            if (nx >= 0 && nx < n && ny >= 0 && ny < m && word[p] == board[nx][ny] && !vt[nx][ny]) {
                vt[nx][ny] = true;
                dfs(board, word, nx, ny, p+1);
                vt[nx][ny] = false;
            }
        }
    }

    bool exist(vector<vector<char>>& board, string word) {
        if (!word.size()) { return true; }
        if (!board.size() || !board[0].size()) { return false; }
        
        n = (int)board.size();
        m = (int)board[0].size();
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                if (board[i][j] == word[0] && !res) {
                    vt[i][j] = true;
                    dfs(board, word, i, j, 1);
                    vt[i][j] = false;
                }
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/word-search/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-search/description/)

Solution: [LeetCode](https://leetcode.com/articles/word-search/)  /  [LeetCode中国](https://leetcode-cn.com/articles/word-search/)