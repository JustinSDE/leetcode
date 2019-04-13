# 167. Two Sum II - Input array is sorted | 两数之和 II - 输入有序数组

## Question description

<!--If you want to use the English description, use <p>Given an array of integers that is already <strong><em>sorted in ascending order</em></strong>, find two numbers such that they add up to a specific target number.</p>

<p>The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>Your returned answers (both index1 and index2) are not zero-based.</li>
	<li>You may assume that each input would have <em>exactly</em> one solution and you may not use the <em>same</em> element twice.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> numbers = [2,7,11,15], target = 9
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.</pre>
 instead-->
<p>给定一个已按照<strong><em>升序排列</em>&nbsp;</strong>的有序数组，找到两个数使得它们相加之和等于目标数。</p>

<p>函数应该返回这两个下标值<em> </em>index1 和 index2，其中 index1&nbsp;必须小于&nbsp;index2<em>。</em></p>

<p><strong>说明:</strong></p>

<ul>
	<li>返回的下标值（index1 和 index2）不是从零开始的。</li>
	<li>你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> numbers = [2, 7, 11, 15], target = 9
<strong>输出:</strong> [1,2]
<strong>解释:</strong> 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。</pre>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        sn = sorted(list(set(numbers)))
        for n in sn:
            if target - n in sn:
                a, b = n, target - n
                break
        i = numbers.index(a)+1
        j = numbers.index(b)+1
        if i == j:
            j = i + 1
        return i, j

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/description/)

Solution: [LeetCode](https://leetcode.com/articles/two-sum-ii-input-array-is-sorted/)  /  [LeetCode中国](https://leetcode-cn.com/articles/two-sum-ii-input-array-is-sorted/)