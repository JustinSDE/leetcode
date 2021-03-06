# 922. Sort Array By Parity II | 按奇偶排序数组 II

## Question description

<!--If you want to use the English description, use <p>Given an array <code>A</code>&nbsp;of non-negative integers, half of the integers in A are odd, and half of the integers are even.</p>

<p>Sort the array so that whenever <code>A[i]</code> is odd, <code>i</code> is odd; and whenever <code>A[i]</code> is even, <code>i</code> is even.</p>

<p>You may return any answer array that satisfies this condition.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[4,2,5,7]</span>
<strong>Output: </strong><span id="example-output-1">[4,5,2,7]</span>
<strong>Explanation: </strong>[4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>2 &lt;= A.length &lt;= 20000</code></li>
	<li><code>A.length % 2 == 0</code></li>
	<li><code>0 &lt;= A[i] &lt;= 1000</code></li>
</ol>

<div>
<p>&nbsp;</p>
</div> instead-->
<p>给定一个非负整数数组&nbsp;<code>A</code>， A 中一半整数是奇数，一半整数是偶数。</p>

<p>对数组进行排序，以便当&nbsp;<code>A[i]</code> 为奇数时，<code>i</code>&nbsp;也是奇数；当&nbsp;<code>A[i]</code>&nbsp;为偶数时， <code>i</code> 也是偶数。</p>

<p>你可以返回任何满足上述条件的数组作为答案。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[4,2,5,7]
<strong>输出：</strong>[4,5,2,7]
<strong>解释：</strong>[4,7,2,5]，[2,5,4,7]，[2,7,4,5] 也会被接受。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>2 &lt;= A.length &lt;= 20000</code></li>
	<li><code>A.length % 2 == 0</code></li>
	<li><code>0 &lt;= A[i] &lt;= 1000</code></li>
</ol>

<p>&nbsp;</p>




## Solution

Language: **python3**  /  Runtime: 164 ms

```python3
class Solution:
    def sortArrayByParityII(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        l1 = list(filter(lambda x: x % 2 == 0, A))
        l2 = list(filter(lambda x: x % 2 == 1, A))
        res = []
        for i in range(len(l1)):
            res.append(l1[i])
            res.append(l2[i])
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sort-array-by-parity-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-array-by-parity-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/sort-array-by-parity-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sort-array-by-parity-ii/)