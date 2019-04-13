# 283. Move Zeroes | 移动零

## Question description

<!--If you want to use the English description, use <p>Given an array <code>nums</code>, write a function to move all <code>0</code>&#39;s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> <code>[0,1,0,3,12]</code>
<b>Output:</b> <code>[1,3,12,0,0]</code></pre>

<p><b>Note</b>:</p>

<ol>
	<li>You must do this <b>in-place</b> without making a copy of the array.</li>
	<li>Minimize the total number of operations.</li>
</ol> instead-->
<p>给定一个数组 <code>nums</code>，编写一个函数将所有 <code>0</code> 移动到数组的末尾，同时保持非零元素的相对顺序。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[0,1,0,3,12]</code>
<strong>输出:</strong> <code>[1,3,12,0,0]</code></pre>

<p><strong>说明</strong>:</p>

<ol>
	<li>必须在原数组上操作，不能拷贝额外的数组。</li>
	<li>尽量减少操作次数。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 188 ms

```python3
class Solution:
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        n = 0
        while 0 in nums:
            nums.remove(0)
            n += 1
        for _ in range(n):
            nums.append(0)

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/move-zeroes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/move-zeroes/description/)

Solution: [LeetCode](https://leetcode.com/articles/move-zeroes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/move-zeroes/)