# 905. Sort Array By Parity | 按奇偶排序数组

## Question description

<!--If you want to use the English description, use <p>Given an array <code>A</code> of non-negative integers, return an array consisting of all the even elements of <code>A</code>, followed by all the odd elements of <code>A</code>.</p>

<p>You may return any answer array that satisfies this condition.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[3,1,2,4]</span>
<strong>Output: </strong><span id="example-output-1">[2,4,3,1]</span>
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 5000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 5000</code></li>
</ol>
</div>
 instead-->
<p>给定一个非负整数数组 <code>A</code>，返回一个由 <code>A</code> 的所有偶数元素组成的数组，后面跟 <code>A</code> 的所有奇数元素。</p>

<p>你可以返回满足此条件的任何数组作为答案。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[3,1,2,4]
<strong>输出：</strong>[2,4,3,1]
输出 [4,2,3,1]，[2,4,1,3] 和 [4,2,1,3] 也会被接受。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 5000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 5000</code></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 128 ms

```python3
class Solution:
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        return list(filter(lambda x: x % 2 == 0, A)) + list(filter(lambda x: x % 2 == 1, A))
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sort-array-by-parity/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-array-by-parity/description/)

Solution: [LeetCode](https://leetcode.com/articles/sort-array-by-parity/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sort-array-by-parity/)