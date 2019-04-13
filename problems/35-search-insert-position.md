# 35. Search Insert Position | 搜索插入位置

## Question description

<!--If you want to use the English description, use <p>Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.</p>

<p>You may assume no duplicates in the array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 5
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 2
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 7
<strong>Output:</strong> 4
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 0
<strong>Output:</strong> 0
</pre>
 instead-->
<p>给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。</p>

<p>你可以假设数组中无重复元素。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 5
<strong>输出:</strong> 2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 2
<strong>输出:</strong> 1
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 7
<strong>输出:</strong> 4
</pre>

<p><strong>示例 4:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 0
<strong>输出:</strong> 0
</pre>




## Solution

Language: **c**  /  Runtime: 3 ms

```c
int searchInsert(int* nums, int numsSize, int target) {
    int pos = 0;
    for (int i = 0; i < numsSize; i++) {
        if (*(nums + i) == target) {
            return i;
        }
        if (*(nums + i) < target) {
            pos = i + 1;
        }
    }
    return pos;
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-insert-position/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-insert-position/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-insert-position/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-insert-position/)