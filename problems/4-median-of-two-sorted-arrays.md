# 4. Median of Two Sorted Arrays | 寻找两个有序数组的中位数

## Question description

<!--If you want to use the English description, use <p>There are two sorted arrays <b>nums1</b> and <b>nums2</b> of size m and n respectively.</p>

<p>Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).</p>

<p>You may assume <strong>nums1</strong> and <strong>nums2</strong>&nbsp;cannot be both empty.</p>

<p><b>Example 1:</b></p>

<pre>
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
</pre>

<p><b>Example 2:</b></p>

<pre>
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
</pre>
 instead-->
<p>给定两个大小为 m 和 n 的有序数组&nbsp;<code>nums1</code> 和&nbsp;<code>nums2</code>。</p>

<p>请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为&nbsp;O(log(m + n))。</p>

<p>你可以假设&nbsp;<code>nums1</code>&nbsp;和&nbsp;<code>nums2</code>&nbsp;不会同时为空。</p>

<p><strong>示例 1:</strong></p>

<pre>nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
</pre>

<p><strong>示例 2:</strong></p>

<pre>nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5
</pre>




## Solution

Language: **python3**  /  Runtime: 92 ms

```python3
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        nums = sorted(nums1 + nums2)
        if len(nums) % 2:
            return nums[len(nums) // 2]
        else:
            return (nums[len(nums) // 2] + nums[len(nums) // 2 - 1]) / 2
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/median-of-two-sorted-arrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/median-of-two-sorted-arrays/)