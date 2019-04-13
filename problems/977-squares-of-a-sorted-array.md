# 977. Squares of a Sorted Array | 有序数组的平方

## Question description

<!--If you want to use the English description, use <p>Given an array of integers <code>A</code>&nbsp;sorted in non-decreasing order,&nbsp;return an array of the squares of each number,&nbsp;also in sorted non-decreasing order.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[-4,-1,0,3,10]</span>
<strong>Output: </strong><span id="example-output-1">[0,1,9,16,100]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[-7,-3,2,3,11]</span>
<strong>Output: </strong><span id="example-output-2">[4,9,9,49,121]</span>
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code><span>1 &lt;= A.length &lt;= 10000</span></code></li>
	<li><code>-10000 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>A</code>&nbsp;is sorted in non-decreasing order.</li>
</ol>
</div>
</div> instead-->
<p>给定一个按非递减顺序排序的整数数组 <code>A</code>，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[-4,-1,0,3,10]
<strong>输出：</strong>[0,1,9,16,100]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[-7,-3,2,3,11]
<strong>输出：</strong>[4,9,9,49,121]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>-10000 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>A</code>&nbsp;已按非递减顺序排序。</li>
</ol>




## Solution

Language: **cpp**  /  Runtime: 88 ms

```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int>& A) {
        vector<int> res;
        int p = 0, t = 0x3f3f3f3f;
        for (int i = 0; i < (int)A.size(); i++) {
            if (abs(A[i]) <= t) {
                p = i;
                t = abs(A[i]);
            } else {
                break;
            }
        }
        res.push_back(A[p] * A[p]);
        int q = p;
        while (p > 0 || q < (int)A.size() - 1) {
            if (p > 0 && q < (int)A.size() - 1) {
                if (abs(A[p - 1]) < abs(A[q + 1])) {
                    p--;
                    res.push_back(A[p] * A[p]);
                } else {
                    q++;
                    res.push_back(A[q] * A[q]);
                }
            } else {
                if (p > 0) {
                    p--;
                    res.push_back(A[p] * A[p]);
                }
                if (q < (int)A.size() - 1) {
                    q++;
                    res.push_back(A[q] * A[q]);
                }
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```

Language: **python3**  /  Runtime: 196 ms

```python3
class Solution:
    def sortedSquares(self, A: List[int]) -> List[int]:
        return sorted(list(map(lambda x : x ** 2, A)))
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/squares-of-a-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/squares-of-a-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/squares-of-a-sorted-array/)