# 74. Search a 2D Matrix | 搜索二维矩阵

## Question description

<!--If you want to use the English description, use <p>Write an efficient algorithm that searches for a value in an <em>m</em> x <em>n</em> matrix. This matrix has the following properties:</p>

<ul>
	<li>Integers in each row are sorted from left to right.</li>
	<li>The first integer of each row is greater than the last integer of the previous row.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
<strong>Output:</strong> false</pre>
 instead-->
<p>编写一个高效的算法来判断&nbsp;<em>m</em> x <em>n</em>&nbsp;矩阵中，是否存在一个目标值。该矩阵具有如下特性：</p>

<ul>
	<li>每行中的整数从左到右按升序排列。</li>
	<li>每行的第一个整数大于前一行的最后一个整数。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
<strong>输出:</strong> false</pre>


## Note

这题很显然用二分法。

用ruby的话，可以一行搞定~


## Solution

Language: **java**  /  Runtime: 0 ms

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
        int i = l;
        l = 0; r = matrix[0].length - 1;
        while (l <= r) {
            int m = l + r >> 1;
            if (matrix[i][m] == target) return true;
            if (matrix[i][m] > target) r = m - 1;
            else l = m + 1;
        }
        return false;
    }
}
```

Language: **ruby**  /  Runtime: 52 ms

```ruby
# @param {Integer[][]} matrix
# @param {Integer} target
# @return {Boolean}
def search_matrix(matrix, target)
    return matrix.flatten.include?(target)
end
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-a-2d-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-a-2d-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-a-2d-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-a-2d-matrix/)