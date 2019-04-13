# 41. First Missing Positive | 缺失的第一个正数

## Question description

<!--If you want to use the English description, use <p>Given an unsorted integer array, find the smallest missing&nbsp;positive integer.</p>

<p><strong>Example 1:</strong></p>

<pre>
Input: [1,2,0]
Output: 3
</pre>

<p><strong>Example 2:</strong></p>

<pre>
Input: [3,4,-1,1]
Output: 2
</pre>

<p><strong>Example 3:</strong></p>

<pre>
Input: [7,8,9,11,12]
Output: 1
</pre>

<p><strong>Note:</strong></p>

<p>Your algorithm should run in <em>O</em>(<em>n</em>) time and uses constant extra space.</p>
 instead-->
<p>给定一个未排序的整数数组，找出其中没有出现的最小的正整数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>输入: [1,2,0]
输出: 3
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>输入: [3,4,-1,1]
输出: 2
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre>输入: [7,8,9,11,12]
输出: 1
</pre>

<p><strong>说明:</strong></p>

<p>你的算法的时间复杂度应为O(<em>n</em>)，并且只能使用常数级别的空间。</p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int p = 0;
        while (p < nums.length) {
            if (nums[p] <= 0 || nums[p] == p + 1) {
                p++;
            } else {
                if (nums[p] > nums.length) {
                    nums[p++] = -1;
                } else {
                    int tmp = nums[nums[p] - 1];
                    if (tmp == nums[p]) {
                        nums[p++] = -1;
                    } else {
                        nums[nums[p] - 1] = nums[p];
                        nums[p] = tmp;
                    }
                }
            }
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] <= 0) return i + 1;
        }
        return nums.length + 1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/first-missing-positive/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-missing-positive/description/)

Solution: [LeetCode](https://leetcode.com/articles/first-missing-positive/)  /  [LeetCode中国](https://leetcode-cn.com/articles/first-missing-positive/)