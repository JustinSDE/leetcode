# 498. Diagonal Traverse | 对角线遍历

## Question description

<!--If you want to use the English description, use <p>Given a matrix of M x N elements (M rows, N columns), return all elements of the matrix in diagonal order as shown in the below image.</p>

<p>&nbsp;</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b>
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]

<b>Output:</b>  [1,2,4,7,5,3,6,8,9]

<b>Explanation:</b>
<img src="https://assets.leetcode.com/uploads/2018/10/12/diagonal_traverse.png" style="width: 220px;" />
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<p>The total number of elements of the given matrix will not exceed 10,000.</p>
 instead-->
<p>给定一个含有 M x N 个元素的矩阵（M 行，N 列），请以对角线遍历的顺序返回这个矩阵中的所有元素，对角线遍历如下图所示。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]

<strong>输出:</strong>  [1,2,4,7,5,3,6,8,9]

<strong>解释:</strong>
<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/diagonal_traverse.png" style="width: 220px;">
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ol>
	<li>给定矩阵中的元素总数不会超过 100000 。</li>
</ol>


## Note

不难，把遍历的过程模拟一下就行，主要是边界情况的处理。


## Solution

Language: **python3**  /  Runtime: 132 ms

```python3
class Solution:
    def findDiagonalOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not matrix or not matrix[0]:
            return []
        upright = True
        res = []
        i, j = 0, 0
        while len(res) < len(matrix) * len(matrix[0]):
            res.append(matrix[i][j])
            if upright:
                if i > 0 and j < len(matrix[0])-1:
                    i -= 1
                    j += 1
                else:
                    upright = False
                    if j == len(matrix[0])-1:
                        i += 1
                    else:
                        j += 1
            else:
                if j > 0 and i < len(matrix)-1:
                    i += 1
                    j -= 1
                else:
                    upright = True
                    if i == len(matrix)-1:
                        j += 1
                    else:
                        i += 1
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/diagonal-traverse/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/diagonal-traverse/description/)

Solution: [LeetCode](https://leetcode.com/articles/diagonal-traverse/)  /  [LeetCode中国](https://leetcode-cn.com/articles/diagonal-traverse/)