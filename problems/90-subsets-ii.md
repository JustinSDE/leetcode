# 90. Subsets II | 子集 II

## Question description

<!--If you want to use the English description, use <p>Given a collection of integers that might contain duplicates, <strong><em>nums</em></strong>, return all possible subsets (the power set).</p>

<p><strong>Note:</strong> The solution set must not contain duplicate subsets.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,2,2]
<strong>Output:</strong>
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
</pre>
 instead-->
<p>给定一个可能包含重复元素的整数数组 <em><strong>nums</strong></em>，返回该数组所有可能的子集（幂集）。</p>

<p><strong>说明：</strong>解集不能包含重复的子集。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,2]
<strong>输出:</strong>
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]</pre>




## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        set<vector<int> > us;
        vector<vector<int> > res;
        vector<int> tmp;
        for (int i=0; i<pow(2, nums.size()); ++i) {
            tmp.clear();
            for (int j=0; j<(int)nums.size(); ++j) {
                if (1 & (i >> j)) {
                    tmp.push_back(nums[j]);
                }
            }
            if (!us.count(tmp)) {
                res.push_back(tmp);
                us.insert(tmp);
            }
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/subsets-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/subsets-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/subsets-ii/)