# 239. Sliding Window Maximum | 滑动窗口最大值

## Question description

<!--If you want to use the English description, use <p>Given an array <em>nums</em>, there is a sliding window of size <em>k</em> which is moving from the very left of the array to the very right. You can only see the <em>k</em> numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> <em>nums</em> = <code>[1,3,-1,-3,5,3,6,7]</code>, and <em>k</em> = 3
<strong>Output: </strong><code>[3,3,5,5,6,7] 
<strong>Explanation: 
</strong></code>
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       <strong>3</strong>
 1 [3  -1  -3] 5  3  6  7       <strong>3</strong>
 1  3 [-1  -3  5] 3  6  7      <strong> 5</strong>
 1  3  -1 [-3  5  3] 6  7       <strong>5</strong>
 1  3  -1  -3 [5  3  6] 7       <strong>6</strong>
 1  3  -1  -3  5 [3  6  7]      <strong>7</strong>
</pre>

<p><strong>Note: </strong><br />
You may assume <em>k</em> is always valid, 1 &le; k &le; input array&#39;s size for non-empty array.</p>

<p><strong>Follow up:</strong><br />
Could you solve it in linear time?</p> instead-->
<p>给定一个数组 <em>nums</em>，有一个大小为&nbsp;<em>k&nbsp;</em>的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口 <em>k</em> 内的数字。滑动窗口每次只向右移动一位。</p>

<p>返回滑动窗口最大值。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <em>nums</em> = <code>[1,3,-1,-3,5,3,6,7]</code>, 和 <em>k</em> = 3
<strong>输出: </strong><code>[3,3,5,5,6,7] 
<strong>解释: 
</strong></code>
  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7</pre>

<p><strong>注意：</strong></p>

<p>你可以假设 <em>k </em>总是有效的，1 &le; k &le;&nbsp;输入数组的大小，且输入数组不为空。</p>

<p><strong>进阶：</strong></p>

<p>你能在线性时间复杂度内解决此题吗？</p>


## Note

![OJ草稿-16-1](https://user-images.githubusercontent.com/9983385/55632833-a9413780-57ed-11e9-97e3-25aa87633b08.jpg)




## Solution

Language: **java**  /  Runtime: 7 ms

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

    public int[] maxSlidingWindow(int[] nums, int k) {
        if (k == 0 || nums.length == 0) return new int[0];
        LinkedList<Node> list = new LinkedList<>();
        int[] ans = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            while (!list.isEmpty() && list.getLast().value <= nums[i]) {
                list.removeLast();
            }
            while (!list.isEmpty() && i - list.getFirst().index >= k) {
                list.removeFirst();
            }
            list.addLast(new Node(i, nums[i]));
            ans[i] = list.getFirst().value;
        }
        return Arrays.copyOfRange(ans, k - 1, ans.length);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sliding-window-maximum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sliding-window-maximum/description/)

Solution: [LeetCode](https://leetcode.com/articles/sliding-window-maximum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sliding-window-maximum/)