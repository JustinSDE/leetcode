# 1010. Pairs of Songs With Total Durations Divisible by 60 | 总持续时间可被 60 整除的歌曲

## Question description

<!--If you want to use the English description, use <p>In a list of songs, the <code>i</code>-th&nbsp;song has a duration of&nbsp;<code>time[i]</code> seconds.&nbsp;</p>

<p>Return the number of pairs of songs for which their total&nbsp;duration in seconds is divisible by <code>60</code>.&nbsp; Formally, we want the number of&nbsp;indices <code>i &lt; j</code> with <code>(time[i] + time[j]) % 60 == 0</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[30,20,150,100,40]</span>
<strong>Output: </strong><span id="example-output-1">3</span>
<strong>Explanation: </strong>Three pairs have a total duration divisible by 60:
(time[0] = 30, time[2] = 150): total duration 180
(time[1] = 20, time[3] = 100): total duration 120
(time[1] = 20, time[4] = 40): total duration 60
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[60,60,60]</span>
<strong>Output: </strong><span id="example-output-2">3</span>
<strong>Explanation: </strong>All three pairs have a total duration of 120, which is divisible by 60.
</pre>
</div>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= time.length &lt;= 60000</code></li>
	<li><code>1 &lt;= time[i] &lt;= 500</code></li>
</ol> instead-->
<p>在歌曲列表中，第 <code>i</code> 首歌曲的持续时间为 <code>time[i]</code> 秒。</p>

<p>返回其总持续时间（以秒为单位）可被 <code>60</code> 整除的歌曲对的数量。形式上，我们希望索引的数字&nbsp;&nbsp;<code>i &lt; j</code> 且有&nbsp;<code>(time[i] + time[j]) % 60 == 0</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[30,20,150,100,40]
<strong>输出：</strong>3
<strong>解释：</strong>这三对的总持续时间可被 60 整数：
(time[0] = 30, time[2] = 150): 总持续时间 180
(time[1] = 20, time[3] = 100): 总持续时间 120
(time[1] = 20, time[4] = 40): 总持续时间 60
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[60,60,60]
<strong>输出：</strong>3
<strong>解释：</strong>所有三对的总持续时间都是 120，可以被 60 整数。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= time.length &lt;= 60000</code></li>
	<li><code>1 &lt;= time[i] &lt;= 500</code></li>
</ol>




## Solution

Language: **python3**  /  Runtime: 60 ms

```python3
class Solution:
    def numPairsDivisibleBy60(self, time: List[int]) -> int:
        # if a > 0, b > 0, (a + b) % m = (a % m + b % m) % m
        res = 0
        d = [0] * 60
        for t in time:
            d[t % 60] += 1
        res += max(0, d[0] * (d[0] - 1) // 2)
        res += max(0, d[30] * (d[30] - 1) // 2)
        for i in range(1, 30):
            res += d[i] * d[60 - i]
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/description/)

Solution: [LeetCode](https://leetcode.com/articles/pairs-of-songs-with-total-durations-divisible-by-60/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pairs-of-songs-with-total-durations-divisible-by-60/)