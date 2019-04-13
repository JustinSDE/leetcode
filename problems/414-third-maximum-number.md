# 414. Third Maximum Number | 第三大的数

## Question description

<!--If you want to use the English description, use <p>Given a <b>non-empty</b> array of integers, return the <b>third</b> maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [3, 2, 1]

<b>Output:</b> 1

<b>Explanation:</b> The third maximum is 1.
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> [1, 2]

<b>Output:</b> 2

<b>Explanation:</b> The third maximum does not exist, so the maximum (2) is returned instead.
</pre>
</p>

<p><b>Example 3:</b><br />
<pre>
<b>Input:</b> [2, 2, 3, 1]

<b>Output:</b> 1

<b>Explanation:</b> Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
</pre>
</p> instead-->
<p>给定一个非空数组，返回此数组中第三大的数。如果不存在，则返回数组中最大的数。要求算法时间复杂度必须是O(n)。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [3, 2, 1]

<strong>输出:</strong> 1

<strong>解释:</strong> 第三大的数是 1.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1, 2]

<strong>输出:</strong> 2

<strong>解释:</strong> 第三大的数不存在, 所以返回最大的数 2 .
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> [2, 2, 3, 1]

<strong>输出:</strong> 1

<strong>解释:</strong> 注意，要求返回第三大的数，是指第三大且唯一出现的数。
存在两个值为2的数，它们都排第二。
</pre>




## Solution

Language: **c**  /  Runtime: 6 ms

```c
int thirdMax(int* nums, int numsSize) {
    int *a[3] = { NULL, NULL, NULL };
    for (int i = 0; i < numsSize; i++, nums++) {
        if (a[0] == NULL) {
            a[0] = nums;
        }
        else {
            if (*nums > *a[0]) {
                if (a[1] == NULL) {
                    a[1] = a[0];
                }
                else {
                    if (*a[1] > *a[0]) {
                        if (a[2] == NULL || *a[0] > *a[2]) {
                            a[2] = a[0];
                        }
                    }
                    if (*a[1] < *a[0]) {
                        if (a[2] == NULL || *a[1] > *a[2]) {
                            a[2] = a[1];
                        }
                        a[1] = a[0];
                    }
                }
                a[0] = nums;
            }
            if (*nums < *a[0]) {
                if (a[1] == NULL) {
                    a[1] = nums;
                }
                else {
                    if (*a[1] > *nums) {
                        if (a[2] == NULL || *a[2] < *nums) {
                            a[2] = nums;
                        }
                    }
                    if (*a[1] < *nums) {
                        if (a[2] == NULL || *a[2] < *a[1]) {
                            a[2] = a[1];
                        }
                        a[1] = nums;
                    }
                }
            }
        }
    }
    if (a[2] == NULL)
        return *a[0];
    else
        return *a[2];
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/third-maximum-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/third-maximum-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/third-maximum-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/third-maximum-number/)