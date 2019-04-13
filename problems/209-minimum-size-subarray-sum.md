# 209. Minimum Size Subarray Sum | 长度最小的子数组

## Question description

<!--If you want to use the English description, use <p>Given an array of <strong>n</strong> positive integers and a positive integer <strong>s</strong>, find the minimal length of a <b>contiguous</b> subarray of which the sum &ge; <strong>s</strong>. If there isn&#39;t one, return 0 instead.</p>

<p><strong>Example:&nbsp;</strong></p>

<pre>
<strong>Input:</strong> <code>s = 7, nums = [2,3,1,2,4,3]</code>
<strong>Output:</strong> 2
<strong>Explanation: </strong>the subarray <code>[4,3]</code> has the minimal length under the problem constraint.</pre>

<div class="spoilers"><b>Follow up:</b></div>

<div class="spoilers">If you have figured out the <i>O</i>(<i>n</i>) solution, try coding another solution of which the time complexity is <i>O</i>(<i>n</i> log <i>n</i>).&nbsp;</div>
 instead-->
<p>给定一个含有&nbsp;<strong>n&nbsp;</strong>个正整数的数组和一个正整数&nbsp;<strong>s ，</strong>找出该数组中满足其和<strong> &ge; s </strong>的长度最小的连续子数组<strong>。</strong>如果不存在符合条件的连续子数组，返回 0。</p>

<p><strong>示例:&nbsp;</strong></p>

<pre><strong>输入:</strong> <code>s = 7, nums = [2,3,1,2,4,3]</code>
<strong>输出:</strong> 2
<strong>解释: </strong>子数组&nbsp;<code>[4,3]</code>&nbsp;是该条件下的长度最小的连续子数组。
</pre>

<p><strong>进阶:</strong></p>

<p>如果你已经完成了<em>O</em>(<em>n</em>) 时间复杂度的解法, 请尝试&nbsp;<em>O</em>(<em>n</em> log <em>n</em>) 时间复杂度的解法。</p>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        if (s > accumulate(nums.begin(), nums.end(), 0)) return 0;
        if (s == 0) return 0;
        vector<int> acc;
        acc.push_back(0);
        for (int n : nums) {
            acc.push_back(n + acc.back());
        }
        int p = 0, q = acc.size() - 1;
        int res = nums.size();
        while (acc[q] - acc[p] >= s && q > p) {
            while (acc[q] - acc[p] >= s) {
                p++;
            }
            p--;
            while (acc[q] - acc[p] >= s) {
                q--;
            }
            q++;
            res = min(res, q - p);
            while (p >=0 && q < acc.size()) {
                p--;
                q--;
                if (acc[q] - acc[p] >= s) {
                    break;
                }
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-size-subarray-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-size-subarray-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-size-subarray-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-size-subarray-sum/)