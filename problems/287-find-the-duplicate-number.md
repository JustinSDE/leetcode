# 287. Find the Duplicate Number | 寻找重复数

## Question description

<!--If you want to use the English description, use <p>Given an array <i>nums</i> containing <i>n</i> + 1 integers where each integer is between 1 and <i>n</i> (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> <code>[1,3,4,2,2]</code>
<b>Output:</b> 2
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [3,1,3,4,2]
<b>Output:</b> 3</pre>

<p><b>Note:</b></p>

<ol>
	<li>You <b>must not</b> modify the array (assume the array is read only).</li>
	<li>You must use only constant, <i>O</i>(1) extra space.</li>
	<li>Your runtime complexity should be less than <em>O</em>(<em>n</em><sup>2</sup>).</li>
	<li>There is only one duplicate number in the array, but it could be repeated more than once.</li>
</ol>
 instead-->
<p>给定一个包含&nbsp;<em>n</em> + 1 个整数的数组&nbsp;<em>nums</em>，其数字都在 1 到 <em>n&nbsp;</em>之间（包括 1 和 <em>n</em>），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[1,3,4,2,2]</code>
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [3,1,3,4,2]
<strong>输出:</strong> 3
</pre>

<p><strong>说明：</strong></p>

<ol>
	<li><strong>不能</strong>更改原数组（假设数组是只读的）。</li>
	<li>只能使用额外的 <em>O</em>(1) 的空间。</li>
	<li>时间复杂度小于 <em>O</em>(<em>n</em><sup>2</sup>) 。</li>
	<li>数组中只有一个重复的数字，但它可能不止重复出现一次。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int p = nums[0], q = nums[nums[0]];
        while (p != q) {
            p = nums[p];
            q = nums[nums[q]];
        }
        q = 0;
        while (p != q) {
            p = nums[p];
            q = nums[q];
        }
        return q;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-the-duplicate-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-duplicate-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-the-duplicate-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-the-duplicate-number/)