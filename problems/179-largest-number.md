# 179. Largest Number | 最大数

## Question description

<!--If you want to use the English description, use <p>Given a list of non negative integers, arrange them such that they form the largest number.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <code>[10,2]</code>
<strong>Output:</strong> &quot;<code>210&quot;</code></pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <code>[3,30,34,5,9]</code>
<strong>Output:</strong> &quot;<code>9534330&quot;</code>
</pre>

<p><strong>Note:</strong> The result may be very large, so you need to return a string instead of an integer.</p>
 instead-->
<p>给定一组非负整数，重新排列它们的顺序使之组成一个最大的整数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[10,2]</code>
<strong>输出:</strong> <code>210</code></pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <code>[3,30,34,5,9]</code>
<strong>输出:</strong> <code>9534330</code></pre>

<p><strong>说明: </strong>输出结果可能非常大，所以你需要返回一个字符串而不是整数。</p>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    string largestNumber(vector<int>& nums) {
        vector<string> ns;
        for (int i : nums){
            ns.push_back(to_string(i));
        }
        auto cmp = [](string& s1, string& s2) { return s1+s2 < s2+s1; };
        sort(ns.begin(), ns.end(), cmp);
        string res;
        for (string s : ns) {
            res = s + res;
        }
        // Remove beginning 0
        string nres;
        bool collect = false;
        for (int i=0; i<res.size(); ++i) {
            if (!collect && (i==res.size()-1) || res[i] != '0' ) {
                collect = true;
            }
            if (collect) {
                nres += res[i];
            }
        }
        return nres;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-number/)