# 80. Remove Duplicates from Sorted Array II | 删除排序数组中的重复项 II

## Question description

<!--If you want to use the English description, use <p>Given a sorted array <em>nums</em>, remove the duplicates <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank"><strong>in-place</strong></a> such that duplicates appeared at most&nbsp;<em>twice</em> and return the new length.</p>

<p>Do not allocate extra space for another array, you must do this by <strong>modifying the input array <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a></strong> with O(1) extra memory.</p>

<p><strong>Example 1:</strong></p>

<pre>
Given <em>nums</em> = <strong>[1,1,1,2,2,3]</strong>,

Your function should return length = <strong><code>5</code></strong>, with the first five elements of <em><code>nums</code></em> being <strong><code>1, 1, 2, 2</code></strong> and <strong>3</strong> respectively.

It doesn&#39;t matter what you leave beyond the returned length.</pre>

<p><strong>Example 2:</strong></p>

<pre>
Given <em>nums</em> = <strong>[0,0,1,1,1,1,2,3,3]</strong>,

Your function should return length = <strong><code>7</code></strong>, with the first seven elements of <em><code>nums</code></em> being modified to&nbsp;<strong><code>0</code></strong>, <strong>0</strong>, <strong>1</strong>, <strong>1</strong>, <strong>2</strong>, <strong>3</strong> and&nbsp;<strong>3</strong> respectively.

It doesn&#39;t matter what values are set beyond&nbsp;the returned length.
</pre>

<p><strong>Clarification:</strong></p>

<p>Confused why the returned value is an integer but your answer is an array?</p>

<p>Note that the input array is passed in by <strong>reference</strong>, which means modification to the input array will be known to the caller as well.</p>

<p>Internally you can think of this:</p>

<pre>
// <strong>nums</strong> is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to <strong>nums</strong> in your function would be known by the caller.
// using the length returned by your function, it prints the first <strong>len</strong> elements.
for (int i = 0; i &lt; len; i++) {
&nbsp; &nbsp; print(nums[i]);
}
</pre>
 instead-->
<p>给定一个排序数组，你需要在<strong><a href="http://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95" target="_blank">原地</a></strong>删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。</p>

<p>不要使用额外的数组空间，你必须在<strong><a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95" target="_blank">原地</a>修改输入数组</strong>并在使用 O(1) 额外空间的条件下完成。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>给定 <em>nums</em> = <strong>[1,1,1,2,2,3]</strong>,

函数应返回新长度 length = <strong><code>5</code></strong>, 并且原数组的前五个元素被修改为 <strong><code>1, 1, 2, 2,</code></strong> <strong>3 </strong>。

你不需要考虑数组中超出新长度后面的元素。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>给定 <em>nums</em> = <strong>[0,0,1,1,1,1,2,3,3]</strong>,

函数应返回新长度 length = <strong><code>7</code></strong>, 并且原数组的前五个元素被修改为&nbsp;<strong><code>0</code></strong>, <strong>0</strong>, <strong>1</strong>, <strong>1</strong>, <strong>2</strong>, <strong>3</strong>, <strong>3 。</strong>

你不需要考虑数组中超出新长度后面的元素。
</pre>

<p><strong>说明:</strong></p>

<p>为什么返回数值是整数，但输出的答案是数组呢?</p>

<p>请注意，输入数组是以<strong>&ldquo;引用&rdquo;</strong>方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。</p>

<p>你可以想象内部操作如下:</p>

<pre>// <strong>nums</strong> 是以&ldquo;引用&rdquo;方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中<strong>该长度范围内</strong>的所有元素。
for (int i = 0; i &lt; len; i++) {
&nbsp; &nbsp; print(nums[i]);
}</pre>




## Solution

Language: **cpp**  /  Runtime: 20 ms

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() < 3) { return nums.size(); }
        int p = 2, q = 2;
        for (; q<(int)nums.size(); ++q) {
            if (nums[q] != nums[p-2]) {
                nums[p++] = nums[q];
            }
        }
        return p;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-duplicates-from-sorted-array-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-duplicates-from-sorted-array-ii/)