# 349. Intersection of Two Arrays | 两个数组的交集

## Question description

<!--If you want to use the English description, use <p>Given two arrays, write a function to compute their intersection.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-1-1">[1,2,2,1]</span>, nums2 = <span id="example-input-1-2">[2,2]</span>
<strong>Output: </strong><span id="example-output-1">[2]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-2-1">[4,9,5]</span>, nums2 = <span id="example-input-2-2">[9,4,9,8,4]</span>
<strong>Output: </strong><span id="example-output-2">[9,4]</span></pre>
</div>

<p><b>Note:</b></p>

<ul>
	<li>Each element in the result must be unique.</li>
	<li>The result can be in any order.</li>
</ul>

<p>&nbsp;</p>
 instead-->
<p>给定两个数组，编写一个函数来计算它们的交集。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>nums1 = [1,2,2,1], nums2 = [2,2]
<strong>输出: </strong>[2]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>nums1 = [4,9,5], nums2 = [9,4,9,8,4]
<strong>输出: </strong>[9,4]</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>输出结果中的每个元素一定是唯一的。</li>
	<li>我们可以不考虑输出结果的顺序。</li>
</ul>




## Solution

Language: **ruby**  /  Runtime: 84 ms

```ruby
# @param {Integer[]} nums1
# @param {Integer[]} nums2
# @return {Integer[]}
def intersection(nums1, nums2)
    nums1 & nums2
end
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/intersection-of-two-arrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/intersection-of-two-arrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/intersection-of-two-arrays/)