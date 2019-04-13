# 229. Majority Element II | 求众数 II

## Question description

<!--If you want to use the English description, use <p>Given an integer array of size <i>n</i>, find all elements that appear more than <code>&lfloor; n/3 &rfloor;</code> times.</p>

<p><strong>Note: </strong>The algorithm should run in linear time and in O(1) space.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,2,3]
<strong>Output:</strong> [3]</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,1,1,3,3,2,2,2]
<strong>Output:</strong> [1,2]</pre>
 instead-->
<p>给定一个大小为&nbsp;<em>n&nbsp;</em>的数组，找出其中所有出现超过&nbsp;<code>&lfloor; n/3 &rfloor;</code>&nbsp;次的元素。</p>

<p><strong>说明: </strong>要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,2,3]
<strong>输出:</strong> [3]</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [1,1,1,3,3,2,2,2]
<strong>输出:</strong> [1,2]</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
// Boyer-Moore Majority Vote  Algorithm
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        if (nums.empty()) return res;
        if (nums.size() < 2) {
            res.push_back(nums[0]);
            return res;
        }
        int n1 = 0, n2 = 0, c1 = 0, c2 = 1;
        for (int i = 0; i < nums.size(); ++i) {
            int n = nums[i];
            if (n == c1) {
                n1++;
            } else if (n == c2) {
                n2++;
            } else if (n1 == 0) {
                c1 = n;
                n1 = 1;
            } else if (n2 == 0) {
                c2 = n;
                n2 = 1;
            } else {
                n1--;
                n2--;
            }
        }
        n1 = 0, n2 = 0;
        for (int n : nums) {
            if (n == c1) {
                n1++;
            } else if (n == c2) {
                n2++;
            }
        }
        if (n1 > nums.size() / 3) {
            res.push_back(c1);
        }
        if (n2 > nums.size() / 3) {
            res.push_back(c2);
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/majority-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/majority-element-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/majority-element-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/majority-element-ii/)