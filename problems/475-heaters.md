# 475. Heaters | 供暖器

## Question description

<!--If you want to use the English description, use <p>Winter is coming! Your first job during the contest is to design a standard heater with fixed warm radius to warm all the houses.</p>

<p>Now, you are given positions of houses and heaters on a horizontal line, find out minimum radius of heaters so that all houses could be covered by those heaters.</p>

<p>So, your input will be the positions of houses and heaters seperately, and your expected output will be the minimum radius standard of heaters.</p>

<p><b>Note:</b></p>

<ol>
	<li>Numbers of houses and heaters you are given are non-negative and will not exceed 25000.</li>
	<li>Positions of houses and heaters you are given are non-negative and will not exceed 10^9.</li>
	<li>As long as a house is in the heaters&#39; warm radius range, it can be warmed.</li>
	<li>All the heaters follow your radius standard and the warm radius will the same.</li>
</ol>

<p>&nbsp;</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [1,2,3],[2]
<b>Output:</b> 1
<b>Explanation:</b> The only heater was placed in the position 2, and if we use the radius 1 standard, then all the houses can be warmed.
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [1,2,3,4],[1,4]
<b>Output:</b> 1
<b>Explanation:</b> The two heater was placed in the position 1 and 4. We need to use radius 1 standard, then all the houses can be warmed.
</pre>

<p>&nbsp;</p>
 instead-->
<p>冬季已经来临。&nbsp;你的任务是设计一个有固定加热半径的供暖器向所有房屋供暖。</p>

<p>现在，给出位于一条水平线上的房屋和供暖器的位置，找到可以覆盖所有房屋的最小加热半径。</p>

<p>所以，你的输入将会是房屋和供暖器的位置。你将输出供暖器的最小加热半径。</p>

<p><strong>说明:</strong></p>

<ol>
	<li>给出的房屋和供暖器的数目是非负数且不会超过 25000。</li>
	<li>给出的房屋和供暖器的位置均是非负数且不会超过10^9。</li>
	<li>只要房屋位于供暖器的半径内(包括在边缘上)，它就可以得到供暖。</li>
	<li>所有供暖器都遵循你的半径标准，加热的半径也一样。</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3],[2]
<strong>输出:</strong> 1
<strong>解释:</strong> 仅在位置2上有一个供暖器。如果我们将加热半径设为1，那么所有房屋就都能得到供暖。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4],[1,4]
<strong>输出:</strong> 1
<strong>解释:</strong> 在位置1, 4上有两个供暖器。我们需要将加热半径设为1，这样所有房屋就都能得到供暖。
</pre>




## Solution

Language: **java**  /  Runtime: 10 ms

```java
class Solution {
    public int findRadius(int[] houses, int[] heaters) {
        Arrays.sort(houses);
        Arrays.sort(heaters);
        int[] heats = new int[heaters.length + 2];
        heats[0] = -0x3f3f3f3f;
        heats[heats.length - 1] = 2 * 0x3f3f3f3f;
        for (int i = 1; i < heats.length - 1; i++) {
            heats[i] = heaters[i - 1];
        }
        int res = 0;
        int left = 0, right = 1;
        for (int h : houses) {
            while (heats[right] <= h) {
                right++;
                left++;
            }
            res = Math.max(res, Math.min(h - heats[left], heats[right] - h));
        }
        return res;
    }
}
```

Language: **python3**  /  Runtime: 124 ms

```python3
class Solution:
    def findRadius(self, houses: List[int], heaters: List[int]) -> int:
        houses.sort()
        heaters.sort()
        heaters.insert(0, float('-inf'))
        heaters.append(float('inf'))
        p = 0
        q = 1
        res = 0
        while p < len(houses) and q < len(heaters):
            if houses[p] < heaters[q]:
                res = max(res, min(heaters[q] - houses[p], houses[p] - heaters[q - 1]))
                p += 1
            else:
                q += 1
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/heaters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/heaters/description/)

Solution: [LeetCode](https://leetcode.com/articles/heaters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/heaters/)