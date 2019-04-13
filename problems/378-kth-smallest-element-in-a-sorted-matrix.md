# 378. Kth Smallest Element in a Sorted Matrix | 有序矩阵中第K小的元素

## Question description

<!--If you want to use the English description, use <p>Given a <i>n</i> x <i>n</i> matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.</p>

<p>
Note that it is the kth smallest element in the sorted order, not the kth distinct element.
</p>

<p><b>Example:</b>
<pre>
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,

return 13.
</pre>
</p>

<p><b>Note: </b><br>
You may assume k is always valid, 1 &le; k &le; n<sup>2</sup>.</p> instead-->
<p>给定一个&nbsp;<em>n x n&nbsp;</em>矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。<br />
请注意，它是排序后的第k小元素，而不是第k个元素。</p>

<p><strong>示例:</strong></p>

<pre>
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,

返回 13。
</pre>

<p><strong>说明: </strong><br />
你可以假设 k 的值永远是有效的, 1 &le; k &le; n<sup>2&nbsp;</sup>。</p>


## Note

用ruby解这题感觉有点不讲道理。


## Solution

Language: **ruby**  /  Runtime: 76 ms

```ruby
# @param {Integer[][]} matrix
# @param {Integer} k
# @return {Integer}
def kth_smallest(matrix, k)
    matrix.flatten.sort.at(k-1)
end
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/kth-smallest-element-in-a-sorted-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/kth-smallest-element-in-a-sorted-matrix/)