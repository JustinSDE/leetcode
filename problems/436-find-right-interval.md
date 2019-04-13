# 436. Find Right Interval | 寻找右区间

## Question description

<!--If you want to use the English description, use <p>
Given a set of intervals, for each of the interval i, check if there exists an interval j whose start point is bigger than or equal to the end point of the interval i, which can be called that j is on the "right" of i.
</p>

<p>
For any interval i, you need to store the minimum interval j's index, which means that the interval j has the minimum start point to build the "right" relationship for interval i. If the interval j doesn't exist, store -1 for the interval i. Finally, you need output the stored value of each interval as an array.
</p>

<p><b>Note:</b><br />
<ol>
<li>You may assume the interval's end point is always bigger than its start point.</li>
<li>You may assume none of these intervals have the same start point.</li>
</ol>
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [ [1,2] ]

<b>Output:</b> [-1]

<b>Explanation:</b> There is only one interval in the collection, so it outputs -1.
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> [ [3,4], [2,3], [1,2] ]

<b>Output:</b> [-1, 0, 1]

<b>Explanation:</b> There is no satisfied "right" interval for [3,4].
For [2,3], the interval [3,4] has minimum-"right" start point;
For [1,2], the interval [2,3] has minimum-"right" start point.
</pre>
</p>

<p><b>Example 3:</b><br />
<pre>
<b>Input:</b> [ [1,4], [2,3], [3,4] ]

<b>Output:</b> [-1, 2, -1]

<b>Explanation:</b> There is no satisfied "right" interval for [1,4] and [3,4].
For [2,3], the interval [3,4] has minimum-"right" start point.
</pre>
</p> instead-->
<p>给定一组区间，对于每一个区间 i，检查是否存在一个区间 j，它的起始点大于或等于区间&nbsp;i 的终点，这可以称为 j 在 i 的&ldquo;右侧&rdquo;。</p>

<p>对于任何区间，你需要存储的满足条件的区间&nbsp;j 的最小索引，这意味着区间 j 有最小的起始点可以使其成为&ldquo;右侧&rdquo;区间。如果区间&nbsp;j 不存在，则将区间 i 存储为 -1。最后，你需要输出一个值为存储的区间值的数组。</p>

<p><strong>注意:</strong></p>

<ol>
	<li>你可以假设区间的终点总是大于它的起始点。</li>
	<li>你可以假定这些区间都不具有相同的起始点。</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [ [1,2] ]
<strong>输出:</strong> [-1]

<strong>解释:</strong>集合中只有一个区间，所以输出-1。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [ [3,4], [2,3], [1,2] ]
<strong>输出:</strong> [-1, 0, 1]

<strong>解释:</strong>对于[3,4]，没有满足条件的&ldquo;右侧&rdquo;区间。
对于[2,3]，区间[3,4]具有最小的&ldquo;右&rdquo;起点;
对于[1,2]，区间[2,3]具有最小的&ldquo;右&rdquo;起点。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> [ [1,4], [2,3], [3,4] ]
<strong>输出:</strong> [-1, 2, -1]

<strong>解释:对于</strong>区间[1,4]和[3,4]，没有满足条件的&ldquo;右侧&rdquo;区间。
对于[2,3]，区间[3,4]有最小的&ldquo;右&rdquo;起点。
</pre>


## Note

![TIM图片20190407094904](https://user-images.githubusercontent.com/9983385/55677462-79dc1900-591a-11e9-9c80-fe38d66b54b8.jpg)




## Solution

Language: **java**  /  Runtime: 14 ms

```java
/**
 * Definition for an interval.
 * public class Interval {
 *     int start;
 *     int end;
 *     Interval() { start = 0; end = 0; }
 *     Interval(int s, int e) { start = s; end = e; }
 * }
 */
class Solution {
    public int[] findRightInterval(Interval[] intervals) {
        List<Integer> index = new ArrayList<>();
        for (int i = 0; i < intervals.length; i++) index.add(i);
        index.sort(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return intervals[o1].start - intervals[o2].start;
            }
        });
        int[] res = new int[intervals.length];
        Arrays.fill(res, -1);
        for (int i = 0; i < index.size(); i++) {
            int idx = index.get(i);
            int target = intervals[idx].end;
            int l = i + 1;
            int r = index.size() - 1;
            while (l < r) {
                int mid = l + r >> 1;
                if (intervals[index.get(mid)].start >= target) r = mid;
                else l = mid + 1;
            }
            if (l < index.size() && intervals[index.get(l)].start >= target) {
                res[idx] = index.get(l);
            }
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-right-interval/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-right-interval/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-right-interval/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-right-interval/)