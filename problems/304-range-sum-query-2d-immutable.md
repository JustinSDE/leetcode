# 304. Range Sum Query 2D - Immutable | 二维区域和检索 - 矩阵不可变

## Question description

<!--If you want to use the English description, use <p>Given a 2D matrix <i>matrix</i>, find the sum of the elements inside the rectangle defined by its upper left corner (<i>row</i>1, <i>col</i>1) and lower right corner (<i>row</i>2, <i>col</i>2).</p>

<p>
<img src="/static/images/courses/range_sum_query_2d.png" border="0" alt="Range Sum Query 2D" /><br />
<small>The above rectangle (with the red border) is defined by (row1, col1) = <b>(2, 1)</b> and (row2, col2) = <b>(4, 3)</b>, which contains sum = <b>8</b>.</small>
</p>

<p><b>Example:</b><br>
<pre>
Given matrix = [
  [3, 0, 1, 4, 2],
  [5, 6, 3, 2, 1],
  [1, 2, 0, 1, 5],
  [4, 1, 0, 1, 7],
  [1, 0, 3, 0, 5]
]

sumRegion(2, 1, 4, 3) -> 8
sumRegion(1, 1, 2, 2) -> 11
sumRegion(1, 2, 2, 4) -> 12
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>You may assume that the matrix does not change.</li>
<li>There are many calls to <i>sumRegion</i> function.</li>
<li>You may assume that <i>row</i>1 &le; <i>row</i>2 and <i>col</i>1 &le; <i>col</i>2.</li>
</ol>
</p> instead-->
<p>给定一个二维矩阵，计算其子矩形范围内元素的总和，该子矩阵的左上角为 (<em>row</em>1,&nbsp;<em>col</em>1) ，右下角为 (<em>row</em>2,&nbsp;<em>col</em>2)。</p>

<p><img alt="Range Sum Query 2D" src="/static/images/courses/range_sum_query_2d.png"><br>
<small>上图子矩阵左上角&nbsp;(row1, col1) = <strong>(2, 1)</strong>&nbsp;，右下角(row2, col2) = <strong>(4, 3)，</strong>该子矩形内元素的总和为 8。</small></p>

<p><strong>示例:</strong></p>

<pre>给定 matrix = [
  [3, 0, 1, 4, 2],
  [5, 6, 3, 2, 1],
  [1, 2, 0, 1, 5],
  [4, 1, 0, 1, 7],
  [1, 0, 3, 0, 5]
]

sumRegion(2, 1, 4, 3) -&gt; 8
sumRegion(1, 1, 2, 2) -&gt; 11
sumRegion(1, 2, 2, 4) -&gt; 12
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>你可以假设矩阵不可变。</li>
	<li>会多次调用&nbsp;<em>sumRegion&nbsp;</em>方法<em>。</em></li>
	<li>你可以假设&nbsp;<em>row</em>1 &le; <em>row</em>2 且&nbsp;<em>col</em>1 &le; <em>col</em>2。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 16 ms

```cpp
class NumMatrix {
public:
    vector<vector<long long> > S;
    NumMatrix(vector<vector<int>> matrix) {
        if (!matrix.size() || !matrix[0].size()) return;
        int n = matrix.size(), m = matrix[0].size();
        S = vector<vector<long long> >(n+1, vector<long long>(m+1, 0));
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                S[i+1][j+1] = matrix[i][j] + S[i+1][j] + S[i][j+1] - S[i][j];
            }
        }
    }
    
    int sumRegion(int row1, int col1, int row2, int col2) {
        return (int)(S[row2+1][col2+1] - S[row1][col2+1] - S[row2+1][col1] + S[row1][col1]);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix obj = new NumMatrix(matrix);
 * int param_1 = obj.sumRegion(row1,col1,row2,col2);
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/range-sum-query-2d-immutable/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-sum-query-2d-immutable/description/)

Solution: [LeetCode](https://leetcode.com/articles/range-sum-query-2d-immutable/)  /  [LeetCode中国](https://leetcode-cn.com/articles/range-sum-query-2d-immutable/)