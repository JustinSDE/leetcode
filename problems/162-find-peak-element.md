# 162. Find Peak Element | 寻找峰值

## Question description

<!--If you want to use the English description, use <p>A peak element is an element that is greater than its neighbors.</p>

<p>Given an input array <code>nums</code>, where <code>nums[i] &ne; nums[i+1]</code>, find a peak element and return its index.</p>

<p>The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.</p>

<p>You may imagine that <code>nums[-1] = nums[n] = -&infin;</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <strong>nums</strong> = <code>[1,2,3,1]</code>
<strong>Output:</strong> 2
<strong>Explanation:</strong> 3 is a peak element and your function should return the index number 2.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <strong>nums</strong> = <code>[</code>1,2,1,3,5,6,4]
<strong>Output:</strong> 1 or 5 
<strong>Explanation:</strong> Your function can return either index number 1 where the peak element is 2, 
&nbsp;            or index number 5 where the peak element is 6.
</pre>

<p><strong>Note:</strong></p>

<p>Your solution should be in logarithmic complexity.</p>
 instead-->
<p>峰值元素是指其值大于左右相邻值的元素。</p>

<p>给定一个输入数组&nbsp;<code>nums</code>，其中 <code>nums[i] &ne; nums[i+1]</code>，找到峰值元素并返回其索引。</p>

<p>数组可能包含多个峰值，在这种情况下，返回任何一个峰值所在位置即可。</p>

<p>你可以假设&nbsp;<code>nums[-1] = nums[n] = -&infin;</code>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <strong>nums</strong> = <code>[1,2,3,1]</code>
<strong>输出:</strong> 2
<strong>解释: </strong>3 是峰值元素，你的函数应该返回其索引 2。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <strong>nums</strong> = <code>[</code>1,2,1,3,5,6,4]
<strong>输出:</strong> 1 或 5 
<strong>解释:</strong> 你的函数可以返回索引 1，其峰值元素为 2；
&nbsp;    或者返回索引 5， 其峰值元素为 6。
</pre>

<p><strong>说明:</strong></p>

<p>你的解法应该是&nbsp;<em>O</em>(<em>logN</em>)<em>&nbsp;</em>时间复杂度的。</p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int findPeakElement(int[] nums) {
        if (nums.length < 2 || nums[0] > nums[1]) return 0;
        int l = 1, r = nums.length - 1;
        while (l < r) {
            int mid = l + r + 1 >> 1;
            if (nums[mid] > nums[mid - 1]) l = mid;
            else r = mid - 1;
        }
        return l;
    }
}
```

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        nums.insert(nums.begin(), INT_MIN);
        nums.push_back(INT_MIN);
        for (int i=1; i<(int)nums.size()-1; ++i) {
            if (nums[i] > nums[i-1] && nums[i] > nums[i+1]) return i-1;
        }
        return nums.size()-3;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-peak-element/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-peak-element/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-peak-element/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-peak-element/)