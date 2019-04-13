# 240. Search a 2D Matrix II | 搜索二维矩阵 II

## Question description

<!--If you want to use the English description, use <p>Write an efficient algorithm that searches for a value in an <i>m</i> x <i>n</i> matrix. This matrix has the following properties:</p>

<ul>
	<li>Integers in each row are sorted in ascending from left to right.</li>
	<li>Integers in each column are sorted in ascending from top to bottom.</li>
</ul>

<p><strong>Example:</strong></p>

<p>Consider the following matrix:</p>

<pre>
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
</pre>

<p>Given&nbsp;target&nbsp;=&nbsp;<code>5</code>, return&nbsp;<code>true</code>.</p>

<p>Given&nbsp;target&nbsp;=&nbsp;<code>20</code>, return&nbsp;<code>false</code>.</p>
 instead-->
<p>编写一个高效的算法来搜索&nbsp;<em>m</em>&nbsp;x&nbsp;<em>n</em>&nbsp;矩阵 matrix 中的一个目标值 target。该矩阵具有以下特性：</p>

<ul>
	<li>每行的元素从左到右升序排列。</li>
	<li>每列的元素从上到下升序排列。</li>
</ul>

<p><strong>示例:</strong></p>

<p>现有矩阵 matrix 如下：</p>

<pre>[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
</pre>

<p>给定 target&nbsp;=&nbsp;<code>5</code>，返回&nbsp;<code>true</code>。</p>

<p>给定&nbsp;target&nbsp;=&nbsp;<code>20</code>，返回&nbsp;<code>false</code>。</p>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0 || matrix[0].length == 0) return false;
        int l = 0, r = matrix.length - 1;
        while (l < r) {
            int m = l + r + 1 >> 1;
            if (matrix[m][0] <= target) l = m;
            else r = m - 1;
        }
        int b = l;
        for (int i = 0; i <= b; i++) {
            l = 0; r = matrix[0].length - 1;
            while (l <= r) {
                int m = l + r >> 1;
                if (matrix[i][m] == target) return true;
                if (matrix[i][m] > target) r = m - 1;
                else l = m + 1;
            }
        }
        return false;
    }
}
```

Language: **ruby**  /  Runtime: 9500 ms

```ruby
# @param {Integer[][]} matrix
# @param {Integer} target
# @return {Boolean}
def search_matrix(matrix, target)
    matrix.flatten.include?(target)
end
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-a-2d-matrix-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-a-2d-matrix-ii/)