# 598. Range Addition II | 范围求和 II

## Question description

<!--If you want to use the English description, use <p>Given an m * n matrix <b>M</b> initialized with all <b>0</b>'s and several update operations.</p>
<p>Operations are represented by a 2D array, and each operation is represented by an array with two <b>positive</b> integers <b>a</b> and <b>b</b>, which means <b>M[i][j]</b> should be <b>added by one</b> for all <b>0 <= i < a</b> and <b>0 <= j < b</b>. </p>
<p>You need to count and return the number of maximum integers in the matrix after performing all the operations.</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> 
m = 3, n = 3
operations = [[2,2],[3,3]]
<b>Output:</b> 4
<b>Explanation:</b> 
Initially, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

After performing [2,2], M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

After performing [3,3], M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

So the maximum integer in M is 2, and there are four of it in M. So return 4.
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The range of m and n is [1,40000].</li>
<li>The range of a is [1,m], and the range of b is [1,n].</li>
<li>The range of operations size won't exceed 10,000.</li>
</ol>
</p> instead-->
<p>给定一个初始元素全部为&nbsp;<strong>0</strong>，大小为 m*n 的矩阵&nbsp;<strong>M&nbsp;</strong>以及在&nbsp;<strong>M&nbsp;</strong>上的一系列更新操作。</p>

<p>操作用二维数组表示，其中的每个操作用一个含有两个<strong>正整数&nbsp;a</strong> 和 <strong>b</strong> 的数组表示，含义是将所有符合&nbsp;<strong>0 &lt;= i &lt; a</strong> 以及 <strong>0 &lt;= j &lt; b</strong> 的元素&nbsp;<strong>M[i][j]&nbsp;</strong>的值都<strong>增加 1</strong>。</p>

<p>在执行给定的一系列操作后，你需要返回矩阵中含有最大整数的元素个数。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 
m = 3, n = 3
operations = [[2,2],[3,3]]
<strong>输出:</strong> 4
<strong>解释:</strong> 
初始状态, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

执行完操作 [2,2] 后, M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

执行完操作 [3,3] 后, M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

M 中最大的整数是 2, 而且 M 中有4个值为2的元素。因此返回 4。
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>m 和 n 的范围是&nbsp;[1,40000]。</li>
	<li>a 的范围是 [1,m]，b 的范围是 [1,n]。</li>
	<li>操作数目不超过 10000。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def maxCount(self, m, n, ops):
        """
        :type m: int
        :type n: int
        :type ops: List[List[int]]
        :rtype: int
        """
        if ops:
            tmp = [_ for _ in zip(*ops)]
            return min(m, min(tmp[0])) * min(n, min(tmp[1]))
        else:
            return m * n

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/range-addition-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-addition-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/range-addition-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/range-addition-ii/)