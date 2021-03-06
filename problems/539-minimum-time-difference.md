# 539. Minimum Time Difference | 最小时间差

## Question description

<!--If you want to use the English description, use Given a list of 24-hour clock time points in "Hour:Minutes" format, find the minimum <b>minutes</b> difference between any two time points in the list. 

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> ["23:59","00:00"]
<b>Output:</b> 1
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The number of time points in the given list is at least 2 and won't exceed 20000.</li>
<li>The input time is legal and ranges from 00:00 to 23:59.</li>
</ol>
</p> instead-->
<p>给定一个 24 小时制（小时:分钟）的时间列表，找出列表中任意两个时间的最小时间差并已分钟数表示。</p>

<p><br />
<strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> [&quot;23:59&quot;,&quot;00:00&quot;]
<strong>输出:</strong> 1
</pre>

<p><br />
<strong>备注:</strong></p>

<ol>
	<li>列表中时间数在 2~20000 之间。</li>
	<li>每个时间取值在 00:00~23:59 之间。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 60 ms

```python3
class Solution:
    def findMinDifference(self, timePoints: List[str]) -> int:
        times = [h * 60 + m for (h, m) in map(lambda tp : tuple(map(int, tp.split(':'))), timePoints)]
        times.sort()
        times.append(1440 + times[0])
        return min([b - a for a, b in zip(times, times[1:])])

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-time-difference/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-time-difference/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-time-difference/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-time-difference/)