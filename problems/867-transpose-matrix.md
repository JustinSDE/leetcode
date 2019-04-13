# 867. Transpose Matrix | 转置矩阵

## Question description

<!--If you want to use the English description, use <p>Given a&nbsp;matrix <code>A</code>, return the transpose of <code>A</code>.</p>

<p>The transpose of a matrix is the matrix flipped over it&#39;s main diagonal, switching the row and column indices of the matrix.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[[1,2,3],[4,5,6],[7,8,9]]</span>
<strong>Output: </strong><span id="example-output-1">[[1,4,7],[2,5,8],[3,6,9]]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[[1,2,3],[4,5,6]]</span>
<strong>Output: </strong><span id="example-output-2">[[1,4],[2,5],[3,6]]</span>
</pre>

<p>&nbsp;</p>

<p><span><strong>Note:</strong></span></p>

<ol>
	<li><code><span>1 &lt;= A.length&nbsp;&lt;= 1000</span></code></li>
	<li><code><span>1 &lt;= A[0].length&nbsp;&lt;= 1000</span></code></li>
</ol>
</div>
</div>
 instead-->
<p>给定一个矩阵&nbsp;<code>A</code>，&nbsp;返回&nbsp;<code>A</code>&nbsp;的转置矩阵。</p>

<p>矩阵的转置是指将矩阵的主对角线翻转，交换矩阵的行索引与列索引。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>[[1,4,7],[2,5,8],[3,6,9]]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6]]
<strong>输出：</strong>[[1,4],[2,5],[3,6]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length&nbsp;&lt;= 1000</code></li>
	<li><code>1 &lt;= A[0].length&nbsp;&lt;= 1000</code></li>
</ol>


## Note

Python里转置矩阵写法非常简单：`list(zip(*A))`


## Solution

Language: **python3**  /  Runtime: 92 ms

```python3
class Solution:
    def transpose(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        return list(zip(*A))
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/transpose-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/transpose-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/transpose-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/transpose-matrix/)