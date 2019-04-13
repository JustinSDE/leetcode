# 1011. Capacity To Ship Packages Within D Days | 在 D 天内送达包裹的能力

## Question description

<!--If you want to use the English description, use <p>A conveyor belt has packages that must be shipped from one port to another within <code>D</code> days.</p>

<p>The <code>i</code>-th package on the conveyor belt has a weight of <code>weights[i]</code>.&nbsp; Each day, we load the ship with packages on the conveyor belt (in the order given by <code>weights</code>). We may not load more weight than the maximum weight capacity of the ship.</p>

<p>Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within <code>D</code> days.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>weights = <span id="example-input-1-1">[1,2,3,4,5,6,7,8,9,10]</span>, D = <span id="example-input-1-2">5</span>
<strong>Output: </strong><span id="example-output-1">15</span>
<strong>Explanation: </strong>
A ship capacity of 15 is the minimum to ship all the packages in 5 days like this:
1st day: 1, 2, 3, 4, 5
2nd day: 6, 7
3rd day: 8
4th day: 9
5th day: 10

Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed. 
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>weights = <span id="example-input-2-1">[3,2,2,4,1,4]</span>, D = <span id="example-input-2-2">3</span>
<strong>Output: </strong><span id="example-output-2">6</span>
<strong>Explanation: </strong>
A ship capacity of 6 is the minimum to ship all the packages in 3 days like this:
1st day: 3, 2
2nd day: 2, 4
3rd day: 1, 4
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>weights = <span id="example-input-3-1">[1,2,3,1,1]</span>, D = 4
<strong>Output: </strong><span id="example-output-3">3</span>
<strong>Explanation: </strong>
1st day: 1
2nd day: 2
3rd day: 3
4th day: 1, 1
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= D &lt;= weights.length &lt;= 50000</code></li>
	<li><code>1 &lt;= weights[i] &lt;= 500</code></li>
</ol> instead-->
<p>传送带上的包裹必须在 D 天内从一个港口运送到另一个港口。</p>

<p>传送带上的第 <code>i</code>&nbsp;个包裹的重量为&nbsp;<code>weights[i]</code>。每一天，我们都会按给出重量的顺序往传送带上装载包裹。我们装载的重量不会超过船的最大运载重量。</p>

<p>返回能在 <code>D</code> 天内将传送带上的所有包裹送达的船的最低运载能力。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>weights = [1,2,3,4,5,6,7,8,9,10], D = 5
<strong>输出：</strong>15
<strong>解释：</strong>
船舶最低载重 15 就能够在 5 天内送达所有包裹，如下所示：
第 1 天：1, 2, 3, 4, 5
第 2 天：6, 7
第 3 天：8
第 4 天：9
第 5 天：10

请注意，货物必须按照给定的顺序装运，因此使用载重能力为 14 的船舶并将包装分成 (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) 是不允许的。 
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>weights = [3,2,2,4,1,4], D = 3
<strong>输出：</strong>6
<strong>解释：</strong>
船舶最低载重 6 就能够在 3 天内送达所有包裹，如下所示：
第 1 天：3, 2
第 2 天：2, 4
第 3 天：1, 4
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>weights = [1,2,3,1,1], D = 4
<strong>输出：</strong>3
<strong>解释：</strong>
第 1 天：1
第 2 天：2
第 3 天：3
第 4 天：1, 1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= D &lt;= weights.length &lt;= 50000</code></li>
	<li><code>1 &lt;= weights[i] &lt;= 500</code></li>
</ol>


## Note

Similar as

875. Koko Eating Bananas

774. Minimize Max Distance to Gas Station




## Solution

Language: **python3**  /  Runtime: 388 ms

```python3
class Solution:
    def shipWithinDays(self, weights: List[int], D: int) -> int:
        left = max(weights)
        right = sum(weights)
        while left < right:
            mid = (left + right) // 2
            days = 1
            shipped = 0
            for w in weights:
                # if cannot take it, take it tomorrow
                if shipped + w > mid:
                    days += 1
                    if days > D:
                        break
                    shipped = 0
                shipped += w
            if days > D:
                left = mid + 1
            else:
                right = mid
        return left

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/capacity-to-ship-packages-within-d-days/description/)

Solution: [LeetCode](https://leetcode.com/articles/capacity-to-ship-packages-within-d-days/)  /  [LeetCode中国](https://leetcode-cn.com/articles/capacity-to-ship-packages-within-d-days/)