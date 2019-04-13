# 137. Single Number II | 只出现一次的数字 II

## Question description

<!--If you want to use the English description, use <p>Given a <strong>non-empty</strong>&nbsp;array of integers, every element appears <em>three</em> times except for one, which appears exactly once. Find that single one.</p>

<p><strong>Note:</strong></p>

<p>Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,2,3,2]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [0,1,0,1,0,1,99]
<strong>Output:</strong> 99</pre>
 instead-->
<p>给定一个<strong>非空</strong>整数数组，除了某个元素只出现一次以外，其余每个元素均出现了三次。找出那个只出现了一次的元素。</p>

<p><strong>说明：</strong></p>

<p>你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [2,2,3,2]
<strong>输出:</strong> 3
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [0,1,0,1,0,1,99]
<strong>输出:</strong> 99</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int singleNumber(int[] nums) {
        int a = 0, b = 0;
        for (int num : nums) {
            a = a ^ num & ~b;
            b = b ^ num & ~a;
        }
        return a | b;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/single-number-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/single-number-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/single-number-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/single-number-ii/)