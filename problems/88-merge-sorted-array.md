# 88. Merge Sorted Array | 合并两个有序数组

## Question description

<!--If you want to use the English description, use <p>Given two sorted integer arrays <em>nums1</em> and <em>nums2</em>, merge <em>nums2</em> into <em>nums1</em> as one sorted array.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The number of elements initialized in <em>nums1</em> and <em>nums2</em> are <em>m</em> and <em>n</em> respectively.</li>
	<li>You may assume that <em>nums1</em> has enough space (size that is greater or equal to <em>m</em> + <em>n</em>) to hold additional elements from <em>nums2</em>.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>Output:</strong>&nbsp;[1,2,2,3,5,6]
</pre>
 instead-->
<p>给定两个有序整数数组&nbsp;<em>nums1 </em>和 <em>nums2</em>，将 <em>nums2 </em>合并到&nbsp;<em>nums1&nbsp;</em>中<em>，</em>使得&nbsp;<em>num1 </em>成为一个有序数组。</p>

<p><strong>说明:</strong></p>

<ul>
	<li>初始化&nbsp;<em>nums1</em> 和 <em>nums2</em> 的元素数量分别为&nbsp;<em>m</em> 和 <em>n</em>。</li>
	<li>你可以假设&nbsp;<em>nums1&nbsp;</em>有足够的空间（空间大小大于或等于&nbsp;<em>m + n</em>）来保存 <em>nums2</em> 中的元素。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>输出:</strong>&nbsp;[1,2,2,3,5,6]</pre>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        while len(nums1) > m:
            nums1.pop()
        nums1.extend(nums2)
        nums1.sort()
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-sorted-array/)