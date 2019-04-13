# 503. Next Greater Element II | 下一个更大元素 II

## Question description

<!--If you want to use the English description, use <p>
Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [1,2,1]
<b>Output:</b> [2,-1,2]
<b>Explanation:</b> The first 1's next greater number is 2; </br>The number 2 can't find next greater number; </br>The second 1's next greater number needs to search circularly, which is also 2.
</pre>
</p>

<p><b>Note:</b>
The length of given array won't exceed 10000.
</p> instead-->
<p>给定一个循环数组（最后一个元素的下一个元素是数组的第一个元素），输出每个元素的下一个更大元素。数字 x 的下一个更大的元素是按数组遍历顺序，这个数字之后的第一个比它更大的数，这意味着你应该循环地搜索它的下一个更大的数。如果不存在，则输出 -1。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,1]
<strong>输出:</strong> [2,-1,2]
<strong>解释:</strong> 第一个 1 的下一个更大的数是 2；
数字 2 找不到下一个更大的数； 
第二个 1 的下一个最大的数需要循环搜索，结果也是 2。
</pre>

<p><strong>注意:</strong> 输入数组的长度不会超过 10000。</p>




## Solution

Language: **python3**  /  Runtime: 216 ms

```python3
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        lnums = nums + nums
        stk = []
        ret = [-1] * len(lnums)
        for i, num in enumerate(lnums):
            while stk and num > stk[-1][1]:
                ret[stk.pop()[0]] = num
            stk.append((i, num))
        res = []
        for i in range(len(nums)):
            t = [ret[i], ret[i + len(nums)]]
            if -1 in t:
                t.remove(-1)
            if t:
                res.append(min(t))
            else:
                res.append(-1)
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/next-greater-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/next-greater-element-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/next-greater-element-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/next-greater-element-ii/)