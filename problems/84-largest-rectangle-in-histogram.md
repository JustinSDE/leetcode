# 84. Largest Rectangle in Histogram | 柱状图中最大的矩形

## Question description

<!--If you want to use the English description, use <p>Given <em>n</em> non-negative integers representing the histogram&#39;s bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/histogram.png" style="width: 188px; height: 204px;" /><br />
<small>Above is a histogram where width of each bar is 1, given height = <code>[2,1,5,6,2,3]</code>.</small></p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/histogram_area.png" style="width: 188px; height: 204px;" /><br />
<small>The largest rectangle is shown in the shaded area, which has area = <code>10</code> unit.</small></p>

<p>&nbsp;</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [2,1,5,6,2,3]
<strong>Output:</strong> 10
</pre>
 instead-->
<p>给定 <em>n</em> 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。</p>

<p>求在该柱状图中，能够勾勒出来的矩形的最大面积。</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/histogram.png"></p>

<p><small>以上是柱状图的示例，其中每个柱子的宽度为 1，给定的高度为&nbsp;<code>[2,1,5,6,2,3]</code>。</small></p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/histogram_area.png"></p>

<p><small>图中阴影部分为所能勾勒出的最大矩形面积，其面积为&nbsp;<code>10</code>&nbsp;个单位。</small></p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [2,1,5,6,2,3]
<strong>输出:</strong> 10</pre>


## Note

![TIM图片20190405122310](https://user-images.githubusercontent.com/9983385/55603521-a61e5b00-579d-11e9-95af-292f79db5eed.jpg)


## Solution

Language: **java**  /  Runtime: 13 ms

```java
class Solution {
    class Node {
        int index;
        int value;
        Node(int index, int value) {
            this.index = index;
            this.value = value;
        }
    }
    
    public int largestRectangleArea(int[] heights) {
        Stack<Node> stk = new Stack<>();
        int[] left = new int[heights.length];
        Arrays.fill(left, -1);
        for (int i = heights.length - 1; i >= 0; i--) {
            while (!stk.empty() && heights[i] < stk.peek().value) {
                left[stk.pop().index] = i;
            }
            stk.push(new Node(i, heights[i]));
        }
        //for (int i : right) System.out.print(i + " "); System.out.println();
        stk.clear();
        int[] right = new int[heights.length];
        Arrays.fill(right, heights.length);
        for (int i = 0; i < heights.length; i++) {
            while (!stk.empty() && heights[i] < stk.peek().value) {
                right[stk.pop().index] = i;
            }
            stk.push(new Node(i, heights[i]));
        }
        //for (int i : right) System.out.print(i + " "); System.out.println();
        int res = 0;
        for (int i = 0; i < heights.length; i++) {
            res = Math.max(res, heights[i] * (right[i] - left[i] - 1));
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-rectangle-in-histogram/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-rectangle-in-histogram/)