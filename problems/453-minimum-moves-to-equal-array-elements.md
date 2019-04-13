# 453. Minimum Moves to Equal Array Elements | 最小移动次数使数组元素相等

## Question description

<!--If you want to use the English description, use <p>Given a <b>non-empty</b> integer array of size <i>n</i>, find the minimum number of moves required to make all array elements equal, where a move is incrementing <i>n</i> - 1 elements by 1.</p>

<p><b>Example:</b>
<pre>
<b>Input:</b>
[1,2,3]

<b>Output:</b>
3

<b>Explanation:</b>
Only three moves are needed (remember each move increments two elements):

[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
</pre>
</p> instead-->
<p>给定一个长度为 <em>n</em> 的<strong>非空</strong>整数数组，找到让数组所有元素相等的最小移动次数。每次移动可以使 <em>n</em> - 1 个元素增加 1。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong>
[1,2,3]

<strong>输出:</strong>
3

<strong>解释:</strong>
只需要3次移动（注意每次移动会增加两个元素的值）：

[1,2,3]  =&gt;  [2,3,3]  =&gt;  [3,4,3]  =&gt;  [4,4,4]
</pre>


## Note

每次操作，其它元素都+1，等效于一个元素相对-1


## Solution

Language: **python3**  /  Runtime: 52 ms

```python3
class Solution:
    def minMoves(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(nums) - min(nums) * len(nums)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-moves-to-equal-array-elements/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-moves-to-equal-array-elements/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-moves-to-equal-array-elements/)