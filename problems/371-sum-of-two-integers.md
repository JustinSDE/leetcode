# 371. Sum of Two Integers | 两整数之和

## Question description

<!--If you want to use the English description, use <p>Calculate the sum of two integers <i>a</i> and <i>b</i>, but you are <b>not allowed</b> to use the operator <code>+</code> and <code>-</code>.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>a = <span id="example-input-1-1">1</span>, b = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">3</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>a = -<span id="example-input-2-1">2</span>, b = <span id="example-input-2-2">3</span>
<strong>Output: </strong>1
</pre>
</div>
</div>
 instead-->
<p><strong>不使用</strong>运算符&nbsp;<code>+</code> 和&nbsp;<code>-</code>&nbsp;​​​​​​​，计算两整数&nbsp;​​​​​​​<code>a</code>&nbsp;、<code>b</code>&nbsp;​​​​​​​之和。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>a = 1, b = 2
<strong>输出: </strong>3
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>a = -2, b = 3
<strong>输出: </strong>1</pre>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    int getSum(int a, int b) {
        if (b == 0) {
            return a;
        } else {
            return getSum(a ^ b, (a & b) << 1);
        }
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sum-of-two-integers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-two-integers/description/)

Solution: [LeetCode](https://leetcode.com/articles/sum-of-two-integers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sum-of-two-integers/)