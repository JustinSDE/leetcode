# 169. Majority Element | 求众数

## Question description

<!--If you want to use the English description, use <p>Given an array of size <i>n</i>, find the majority element. The majority element is the element that appears <b>more than</b> <code>&lfloor; n/2 &rfloor;</code> times.</p>

<p>You may assume that the array is non-empty and the majority element always exist in the array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,2,3]
<strong>Output:</strong> 3</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [2,2,1,1,1,2,2]
<strong>Output:</strong> 2
</pre>
 instead-->
<p>给定一个大小为 <em>n </em>的数组，找到其中的众数。众数是指在数组中出现次数<strong>大于</strong>&nbsp;<code>&lfloor; n/2 &rfloor;</code>&nbsp;的元素。</p>

<p>你可以假设数组是非空的，并且给定的数组总是存在众数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,2,3]
<strong>输出:</strong> 3</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [2,2,1,1,1,2,2]
<strong>输出:</strong> 2
</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
// Boyer-Moore Majority Vote Algorithm
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = 0, c = 0;
        for (int i : nums) {
            if (i == c) {
                n++;
            } else if (n == 0) {
                c = i;
                n = 1;
            } else {
                n--;
            }
        }
        return c;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```

Language: **python3**  /  Runtime: 52 ms

```python3
class Solution:
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sorted([(k, v) for k, v in collections.Counter(nums).items()], key=lambda x: x[1], reverse=True)[0][0]
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/majority-element/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/majority-element/description/)

Solution: [LeetCode](https://leetcode.com/articles/majority-element/)  /  [LeetCode中国](https://leetcode-cn.com/articles/majority-element/)