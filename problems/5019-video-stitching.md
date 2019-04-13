# 5019. Video Stitching | 视频拼接

## Question description

<!--If you want to use the English description, use <p>You are given a series of video clips from a sporting event that lasted <code>T</code> seconds.&nbsp;&nbsp;These video clips can be overlapping with each other and have varied lengths.</p>

<p>Each video clip <code>clips[i]</code>&nbsp;is an interval: it starts at time <code>clips[i][0]</code> and ends at time <code>clips[i][1]</code>.&nbsp; We can cut these clips into segments freely: for example, a clip <code>[0, 7]</code> can be cut into segments&nbsp;<code>[0, 1] +&nbsp;[1, 3] + [3, 7]</code>.</p>

<p>Return the minimum number of clips needed so that we can cut the clips into segments that cover the entire sporting event (<code>[0, T]</code>).&nbsp; If the task is impossible, return <code>-1</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>clips = <span id="example-input-1-1">[[0,2],[4,6],[8,10],[1,9],[1,5],[5,9]]</span>, T = <span id="example-input-1-2">10</span>
<strong>Output: </strong><span id="example-output-1">3</span>
<strong>Explanation: </strong>
We take the clips [0,2], [8,10], [1,9]; a total of 3 clips.
Then, we can reconstruct the sporting event as follows:
We cut [1,9] into segments [1,2] + [2,8] + [8,9].
Now we have segments [0,2] + [2,8] + [8,10] which cover the sporting event [0, 10].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>clips = <span id="example-input-2-1">[[0,1],[1,2]]</span>, T = <span id="example-input-2-2">5</span>
<strong>Output: </strong><span id="example-output-2">-1</span>
<strong>Explanation: </strong>
We can&#39;t cover [0,5] with only [0,1] and [0,2].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>clips = <span id="example-input-3-1">[[0,1],[6,8],[0,2],[5,6],[0,4],[0,3],[6,7],[1,3],[4,7],[1,4],[2,5],[2,6],[3,4],[4,5],[5,7],[6,9]]</span>, T = <span id="example-input-3-2">9</span>
<strong>Output: </strong><span id="example-output-3">3</span>
<strong>Explanation: </strong>
We can take clips [0,4], [4,7], and [6,9].
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong>clips = <span id="example-input-4-1">[[0,4],[2,8]]</span>, T = <span id="example-input-4-2">5</span>
<strong>Output: </strong><span id="example-output-4">2</span>
<strong>Explanation: </strong>
Notice you can have extra video after the event ends.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= clips.length &lt;= 100</code></li>
	<li><code>0 &lt;= clips[i][0], clips[i][1] &lt;= 100</code></li>
	<li><code>0 &lt;= T &lt;= 100</code></li>
</ol> instead-->
<p>你将会获得一系列视频片段，这些片段来自于一项持续时长为&nbsp;<code>T</code>&nbsp;秒的体育赛事。这些片段可能有所重叠，也可能长度不一。</p>

<p>视频片段&nbsp;<code>clips[i]</code>&nbsp;都用区间进行表示：开始于&nbsp;<code>clips[i][0]</code>&nbsp;并于&nbsp;<code>clips[i][1]</code>&nbsp;结束。我们甚至可以对这些片段自由地再剪辑，例如片段&nbsp;<code>[0, 7]</code>&nbsp;可以剪切成&nbsp;<code>[0, 1] +&nbsp;[1, 3] + [3, 7]</code>&nbsp;三部分。</p>

<p>我们需要将这些片段进行再剪辑，并将剪辑后的内容拼接成覆盖整个运动过程的片段（<code>[0, T]</code>）。返回所需片段的最小数目，如果无法完成该任务，则返回&nbsp;<code>-1</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>clips = [[0,2],[4,6],[8,10],[1,9],[1,5],[5,9]], T = 10
<strong>输出：</strong>3
<strong>解释：</strong>
我们选中 [0,2], [8,10], [1,9] 这三个片段。
然后，按下面的方案重制比赛片段：
将 [1,9] 再剪辑为 [1,2] + [2,8] + [8,9] 。
现在我们手上有 [0,2] + [2,8] + [8,10]，而这些涵盖了整场比赛 [0, 10]。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>clips = [[0,1],[1,2]], T = 5
<strong>输出：</strong>-1
<strong>解释：</strong>
我们无法只用 [0,1] 和 [0,2] 覆盖 [0,5] 的整个过程。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>clips = [[0,1],[6,8],[0,2],[5,6],[0,4],[0,3],[6,7],[1,3],[4,7],[1,4],[2,5],[2,6],[3,4],[4,5],[5,7],[6,9]], T = 9
<strong>输出：</strong>3
<strong>解释： </strong>
我们选取片段 [0,4], [4,7] 和 [6,9] 。
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>clips = [[0,4],[2,8]], T = 5
<strong>输出：</strong>2
<strong>解释：</strong>
注意，你可能录制超过比赛结束时间的视频。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= clips.length &lt;= 100</code></li>
	<li><code>0 &lt;= clips[i][0], clips[i][1] &lt;= 100</code></li>
	<li><code>0 &lt;= T &lt;= 100</code></li>
</ol>


## Note

![TIM图片20190408221327](https://user-images.githubusercontent.com/9983385/55730861-b3f90800-5a4b-11e9-83fa-68666ee1d744.jpg)


## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def videoStitching(self, clips: List[List[int]], T: int) -> int:
        # 边界情况
        if (len(clips) == 0):
            return T == 0
        elif (len(clips) == 1):
            return clips[0][0] == 0 and clips[0][1] == T

        clips.sort(key=lambda c : c[0])
        # 设范围被包含的片段为无效片段，仅考虑有效片段
        valid = [True] * len(clips)
        for i in range(len(clips) - 1):
            if valid[i]:
                for j in range(i + 1, len(clips)):
                    # j 为无效片段
                    if clips[i][0] <= clips[j][0] and clips[i][1] >= clips[j][1]:
                        valid[j] = False
                    # i 为无效片段
                    elif clips[j][0] <= clips[i][0] and clips[j][1] >= clips[i][1]:
                        valid[i] = False;
                        break
                    # 必然不会包含，跳过后续比较
                    elif clips[i][1] >= clips[j][0]:
                        break
        
        valid_clips = [clips[i] for i in range(len(clips)) if valid[i]]
        # 若某个时间点只有一个有效片段，则该片段必选
        # 若存在多个可选的片段，选择最迟结束的片段
        t = 0  # 检查时间点
        pre = -1  # 前一片段索引
        res = 0
        while t < T:
            avail = []
            for i in range(pre + 1, len(valid_clips)):
                if valid_clips[i][0] <= t <= valid_clips[i][1]:
                    avail.append(i)
                else:
                    break
            if not avail:
                return -1
            avail.sort(key=lambda x : -1 * valid_clips[x][1])
            res += 1
            pre = avail[0]
            t = valid_clips[pre][1]
        return res   
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/video-stitching/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/video-stitching/description/)

Solution: [LeetCode](https://leetcode.com/articles/video-stitching/)  /  [LeetCode中国](https://leetcode-cn.com/articles/video-stitching/)