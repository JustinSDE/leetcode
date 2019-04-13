# 223. Rectangle Area | 矩形面积

## Question description

<!--If you want to use the English description, use <p>Find the total area covered by two <strong>rectilinear</strong> rectangles in a <strong>2D</strong> plane.</p>

<p>Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.</p>

<p><img alt="Rectangle Area" src="https://assets.leetcode.com/uploads/2018/10/22/rectangle_area.png" style="width: 542px; height: 304px;" /></p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">-3</span>, B = <span id="example-input-1-2">0</span>, C = <span id="example-input-1-3">3</span>, D = <span id="example-input-1-4">4</span>, E = <span id="example-input-1-5">0</span>, F = <span id="example-input-1-6">-1</span>, G = <span id="example-input-1-7">9</span>, H = <span id="example-input-1-8">2</span>
<strong>Output: </strong><span id="example-output-1">45</span></pre>

<p><strong>Note:</strong></p>

<p>Assume that the total area is never beyond the maximum possible value of <strong>int</strong>.</p>
 instead-->
<p>在<strong>二维</strong>平面上计算出两个<strong>由直线构成的</strong>矩形重叠后形成的总面积。</p>

<p>每个矩形由其左下顶点和右上顶点坐标表示，如图所示。</p>

<p><img alt="Rectangle Area" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rectangle_area.png"></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> -3, 0, 3, 4, 0, -1, 9, 2
<strong>输出:</strong> 45</pre>

<p><strong>说明:</strong> 假设矩形面积不会超出&nbsp;<strong>int&nbsp;</strong>的范围。</p>




## Solution

Language: **cpp**  /  Runtime: 16 ms

```cpp
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int area1 = (C - A) * (D - B);
        int area2 = (G - E) * (H - F);
        if (C <= E || D <= F || H <= B || G <= A) {
            return area1 + area2;
        } else {
            int area3 = (min(C, G) - max(A, E)) * (min(D, H) - max(B, F));
            return area1 + area2 - area3;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/rectangle-area/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rectangle-area/description/)

Solution: [LeetCode](https://leetcode.com/articles/rectangle-area/)  /  [LeetCode中国](https://leetcode-cn.com/articles/rectangle-area/)