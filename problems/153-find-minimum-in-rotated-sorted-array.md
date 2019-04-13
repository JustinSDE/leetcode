# 153. Find Minimum in Rotated Sorted Array | 寻找旋转排序数组中的最小值

## Question description

<!--If you want to use the English description, use <p>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</p>

<p>(i.e., &nbsp;<code>[0,1,2,4,5,6,7]</code>&nbsp;might become &nbsp;<code>[4,5,6,7,0,1,2]</code>).</p>

<p>Find the minimum element.</p>

<p>You may assume no duplicate exists in the array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,4,5,1,2] 
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,5,6,7,0,1,2]
<strong>Output:</strong> 0
</pre>
 instead-->
<p>假设按照升序排序的数组在预先未知的某个点上进行了旋转。</p>

<p>( 例如，数组&nbsp;<code>[0,1,2,4,5,6,7]</code> <strong> </strong>可能变为&nbsp;<code>[4,5,6,7,0,1,2]</code>&nbsp;)。</p>

<p>请找出其中最小的元素。</p>

<p>你可以假设数组中不存在重复元素。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [3,4,5,1,2]
<strong>输出:</strong> 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [4,5,6,7,0,1,2]
<strong>输出:</strong> 0</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int findMin(int[] nums) {
        int l = 0, r = nums.length - 1;
        while (l < r) {
            int mid = l + r >> 1;
            if (nums[mid] <= nums[r]) r = mid;
            else l = mid + 1;
        }
        return nums[l];
    }
}
```

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        return *min_element(nums.begin(), nums.end());
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-minimum-in-rotated-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-minimum-in-rotated-sorted-array/)