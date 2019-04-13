# 718. Maximum Length of Repeated Subarray | 最长重复子数组

## Question description

<!--If you want to use the English description, use <p>Given two integer arrays <code>A</code> and <code>B</code>, return the maximum length of an subarray that appears in both arrays.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b>
A: [1,2,3,2,1]
B: [3,2,1,4,7]
<b>Output:</b> 3
<b>Explanation:</b> 
The repeated subarray with maximum length is [3, 2, 1].
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>1 &lt;= len(A), len(B) &lt;= 1000</li>
	<li>0 &lt;= A[i], B[i] &lt; 100</li>
</ol>

<p>&nbsp;</p>
 instead-->
<p>给两个整数数组&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;，返回两个数组中公共的、长度最长的子数组的长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
A: [1,2,3,2,1]
B: [3,2,1,4,7]
<strong>输出:</strong> 3
<strong>解释:</strong> 
长度最长的公共子数组是 [3, 2, 1]。
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>1 &lt;= len(A), len(B) &lt;= 1000</li>
	<li>0 &lt;= A[i], B[i] &lt; 100</li>
</ol>




## Solution

Language: **java**  /  Runtime: 15 ms

```java
class Solution {
    public int findLength(int[] A, int[] B) {
        int[] dp = new int[B.length + 1];
        int res = 0;
        for (int i = 0; i < A.length; i++) {
            for (int j = B.length - 1; j >= 0; j--) {
                dp[j + 1] = A[i] == B[j] ? dp[j] + 1 : 0;
                res = Math.max(res, dp[j + 1]);
            }
        }     
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-length-of-repeated-subarray/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-length-of-repeated-subarray/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-length-of-repeated-subarray/)