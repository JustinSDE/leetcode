# 739. Daily Temperatures | 每日温度

## Question description

<!--If you want to use the English description, use <p>
Given a list of daily temperatures <code>T</code>, return a list such that, for each day in the input, tells you how many days you would have to wait until a warmer temperature.  If there is no future day for which this is possible, put <code>0</code> instead.
</p><p>
For example, given the list of temperatures <code>T = [73, 74, 75, 71, 69, 72, 76, 73]</code>, your output should be <code>[1, 1, 4, 2, 1, 1, 0, 0]</code>.
</p>

<p><b>Note:</b>
The length of <code>temperatures</code> will be in the range <code>[1, 30000]</code>.
Each temperature will be an integer in the range <code>[30, 100]</code>.
</p> instead-->
<p>根据每日 <code>气温</code> 列表，请重新生成一个列表，对应位置的输入是你需要再等待多久温度才会升高的天数。如果之后都不会升高，请输入&nbsp;<code>0</code> 来代替。</p>

<p>例如，给定一个列表&nbsp;<code>temperatures = [73, 74, 75, 71, 69, 72, 76, 73]</code>，你的输出应该是&nbsp;<code>[1, 1, 4, 2, 1, 1, 0, 0]</code>。</p>

<p><strong>提示：</strong><code>气温</code> 列表长度的范围是&nbsp;<code>[1, 30000]</code>。每个气温的值的都是&nbsp;<code>[30, 100]</code>&nbsp;范围内的整数。</p>




## Solution

Language: **python3**  /  Runtime: 848 ms

```python3
class Solution:
    def dailyTemperatures(self, temperatures):
        """
        :type temperatures: List[int]
        :rtype: List[int]
        """
        res = []
        tds = [float('inf')] * (100 - 30 + 2)
        for i in range(len(temperatures)-1, -1, -1):
            t = temperatures[i]
            v = min(tds[t-30+1:]) - i
            if v == float('inf'):
                res.append(0)
            else:
                res.append(v)
            tds[t-30] = i
        res.reverse()
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/daily-temperatures/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/daily-temperatures/description/)

Solution: [LeetCode](https://leetcode.com/articles/daily-temperatures/)  /  [LeetCode中国](https://leetcode-cn.com/articles/daily-temperatures/)