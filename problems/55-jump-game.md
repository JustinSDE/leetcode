# 55. Jump Game | 跳跃游戏

## Question description

<!--If you want to use the English description, use <p>Given an array of non-negative integers, you are initially positioned at the first index of the array.</p>

<p>Each element in the array represents your maximum jump length at that position.</p>

<p>Determine if you are able to reach the last index.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,1,1,4]
<strong>Output:</strong> true
<strong>Explanation:</strong> Jump 1 step from index 0 to 1, then 3 steps to the last index.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [3,2,1,0,4]
<strong>Output:</strong> false
<strong>Explanation:</strong> You will always arrive at index 3 no matter what. Its maximum
&nbsp;            jump length is 0, which makes it impossible to reach the last index.
</pre>
 instead-->
<p>给定一个非负整数数组，你最初位于数组的第一个位置。</p>

<p>数组中的每个元素代表你在该位置可以跳跃的最大长度。</p>

<p>判断你是否能够到达最后一个位置。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [2,3,1,1,4]
<strong>输出:</strong> true
<strong>解释:</strong> 从位置 0 到 1 跳 1 步, 然后跳 3 步到达最后一个位置。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [3,2,1,0,4]
<strong>输出:</strong> false
<strong>解释:</strong> 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。
</pre>


## Note

一开始寻思着用DFS做，结果各种超时。经过分析之后感觉DFS确实不适合，除了复杂度比较高（基本就是暴力），在不能抵达终点时容易出现死循环。

还是要看最远可抵达索引，也就是采用贪心策略，当最远可抵达处为0时表示无法继续前进了。

注意，当终点为0时依然算可行的。


## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if len(nums) < 2:
            return True
        if nums.count(0) == 0:
            return True
        mi = 0
        for i, num in enumerate(nums):
            if i + num < mi:
                continue
            if num > 0:
                mi = i + num
            else:
                return False or i == len(nums) - 1
        return mi >= len(nums) - 1

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/jump-game/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jump-game/description/)

Solution: [LeetCode](https://leetcode.com/articles/jump-game/)  /  [LeetCode中国](https://leetcode-cn.com/articles/jump-game/)