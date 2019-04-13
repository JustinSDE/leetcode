# 342. Power of Four | 4的幂

## Question description

<!--If you want to use the English description, use <p>Given an integer (signed 32 bits), write a function to check whether it is a power of 4.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">16</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">5</span>
<strong>Output: </strong><span id="example-output-2">false</span></pre>
</div>

<p><b>Follow up</b>: Could you solve it without loops/recursion?</p> instead-->
<p>给定一个整数 (32 位有符号整数)，请编写一个函数来判断它是否是 4&nbsp;的幂次方。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>16
<strong>输出: </strong>true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>5
<strong>输出: </strong>false</pre>

<p><strong>进阶：</strong><br>
你能不使用循环或者递归来完成本题吗？</p>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    bool isPowerOfFour(int num) {
        return num > 0 && !(num & (num - 1)) && !((num - 1) % 3); 
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/power-of-four/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/power-of-four/description/)

Solution: [LeetCode](https://leetcode.com/articles/power-of-four/)  /  [LeetCode中国](https://leetcode-cn.com/articles/power-of-four/)