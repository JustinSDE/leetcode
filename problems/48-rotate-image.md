# 48. Rotate Image | 旋转图像

## Question description

<!--If you want to use the English description, use <p>You are given an <em>n</em> x <em>n</em> 2D matrix representing an image.</p>

<p>Rotate the image by 90 degrees (clockwise).</p>

<p><strong>Note:</strong></p>

<p>You have to rotate the image <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank"><strong>in-place</strong></a>, which means you have to modify the input 2D matrix directly. <strong>DO NOT</strong> allocate another 2D matrix and do the rotation.</p>

<p><strong>Example 1:</strong></p>

<pre>
Given <strong>input matrix</strong> = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix <strong>in-place</strong> such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
Given <strong>input matrix</strong> =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix <strong>in-place</strong> such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
</pre>
 instead-->
<p>给定一个 <em>n&nbsp;</em>&times;&nbsp;<em>n</em> 的二维矩阵表示一个图像。</p>

<p>将图像顺时针旋转 90 度。</p>

<p><strong>说明：</strong></p>

<p>你必须在<strong><a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95" target="_blank">原地</a></strong>旋转图像，这意味着你需要直接修改输入的二维矩阵。<strong>请不要</strong>使用另一个矩阵来旋转图像。</p>

<p><strong>示例 1:</strong></p>

<pre>给定 <strong>matrix</strong> = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

<strong>原地</strong>旋转输入矩阵，使其变为:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
</pre>

<p><strong>示例 2:</strong></p>

<pre>给定 <strong>matrix</strong> =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

<strong>原地</strong>旋转输入矩阵，使其变为:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
</pre>


## Note

如果不要求原地修改，用Python就一行的事。


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    void swap(int& x, int& y) {
        x ^= y;
        y ^= x;
        x ^= y;
    }

    void rotateRing(vector<vector<int>>& m, int p, int q) {
        int j = q - p;
        if (!j) { return; }
        // swap corner
        swap(m[p][p], m[p][q]);
        swap(m[p][p], m[q][q]);
        swap(m[p][p], m[q][p]);
        if (j == 1) { return; }

        // swap top & right
        for (int i=1; i<j; ++i) {
            swap(m[p][p+i], m[p+i][q]);
        }
        // swap bottom & left
        for (int i=1; i<j; ++i) {
            swap(m[q][p+i], m[p+i][p]);
        }
        // swap top & bottom
        for (int i=1; i<j; ++i) {
            swap(m[p][p+i], m[q][q-i]);
        }
    }

    void rotate(vector<vector<int>>& matrix) {
        if (!matrix.empty() && !matrix[0].empty()) {
            int n = (int)matrix.size();
            for (int i=0, j=n-1; i<=j; ++i, --j) {
                rotateRing(matrix, i, j);
            }
        }
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/rotate-image/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rotate-image/description/)

Solution: [LeetCode](https://leetcode.com/articles/rotate-image/)  /  [LeetCode中国](https://leetcode-cn.com/articles/rotate-image/)