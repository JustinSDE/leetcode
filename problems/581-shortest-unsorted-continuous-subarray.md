# 581. Shortest Unsorted Continuous Subarray | 最短无序连续子数组

## Question description

<!--If you want to use the English description, use <p>Given an integer array, you need to find one <b>continuous subarray</b> that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order, too. </p> 

<p>You need to find the <b>shortest</b> such subarray and output its length.</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [2, 6, 4, 8, 10, 9, 15]
<b>Output:</b> 5
<b>Explanation:</b> You need to sort [6, 4, 8, 10, 9] in ascending order to make the whole array sorted in ascending order.
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>Then length of the input array is in range [1, 10,000].</li>
<li>The input array may contain duplicates, so ascending order here means <b><=</b>. </li>
</ol>
</p> instead-->
<p>给定一个整数数组，你需要寻找一个<strong>连续的子数组</strong>，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。</p>

<p>你找到的子数组应是<strong>最短</strong>的，请输出它的长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [2, 6, 4, 8, 10, 9, 15]
<strong>输出:</strong> 5
<strong>解释:</strong> 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。
</pre>

<p><strong>说明 :</strong></p>

<ol>
	<li>输入的数组长度范围在&nbsp;[1, 10,000]。</li>
	<li>输入的数组可能包含<strong>重复</strong>元素&nbsp;，所以<strong>升序</strong>的意思是<strong>&lt;=。</strong></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 124 ms

```python3
class Solution:
    def findUnsortedSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        '''
        排序前：[2, 6, 4, 8, 10,  9, 15]
        排序后：[2, 4, 6, 8,  9, 10, 15]
        思路：排序前后首尾比对
        '''
        snums = sorted(nums)
        cnt = 0
        for i in range(len(nums)):
            if nums[i] == snums[i]:
                cnt += 1
            else:
                break
        for j in range(len(nums)-1, i, -1):
            if nums[j] == snums[j]:
                cnt += 1
            else:
                break
        return len(nums) - cnt
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/description/)

Solution: [LeetCode](https://leetcode.com/articles/shortest-unsorted-continuous-subarray/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shortest-unsorted-continuous-subarray/)