# 89. Gray Code | 格雷编码

## Question description

<!--If you want to use the English description, use <p>The gray code is a binary numeral system where two successive values differ in only one bit.</p>

<p>Given a non-negative integer <em>n</em> representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;2
<strong>Output:</strong>&nbsp;<code>[0,1,3,2]</code>
<strong>Explanation:</strong>
00 - 0
01 - 1
11 - 3
10 - 2

For a given&nbsp;<em>n</em>, a gray code sequence may not be uniquely defined.
For example, [0,2,3,1] is also a valid gray code sequence.

00 - 0
10 - 2
11 - 3
01 - 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;0
<strong>Output:</strong>&nbsp;<code>[0]
<strong>Explanation:</strong> We define the gray code sequence to begin with 0.
&nbsp;            A gray code sequence of <em>n</em> has size = 2<sup>n</sup>, which for <em>n</em> = 0 the size is 2<sup>0</sup> = 1.
&nbsp;            Therefore, for <em>n</em> = 0 the gray code sequence is [0].</code>
</pre>
 instead-->
<p>格雷编码是一个二进制数字系统，在该系统中，两个连续的数值仅有一个位数的差异。</p>

<p>给定一个代表编码总位数的非负整数<em> n</em>，打印其格雷编码序列。格雷编码序列必须以 0 开头。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>&nbsp;2
<strong>输出:</strong>&nbsp;<code>[0,1,3,2]</code>
<strong>解释:</strong>
00 - 0
01 - 1
11 - 3
10 - 2

对于给定的&nbsp;<em>n</em>，其格雷编码序列并不唯一。
例如，<code>[0,2,3,1]</code>&nbsp;也是一个有效的格雷编码序列。

00 - 0
10 - 2
11 - 3
01 - 1</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>&nbsp;0
<strong>输出:</strong>&nbsp;<code>[0]
<strong>解释:</strong> 我们定义</code>格雷编码序列必须以 0 开头。<code>
&nbsp;    给定</code>编码总位数为<code> <em>n</em> 的格雷编码序列，其长度为 2<sup>n</sup></code>。<code>当 <em>n</em> = 0 时，长度为 2<sup>0</sup> = 1。
&nbsp;    因此，当 <em>n</em> = 0 时，其格雷编码序列为 [0]。</code>
</pre>


## Note

将x的二进制第n位取反：`x^(i<<n)`


## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
class Solution {
public:
    vector<int> res;
    unordered_set<int> vt;
    void dfs(int n, int x) {
        if (res.size() == pow(2, n)) {
            return;
        }
        for (int i=0; i<n; ++i) {
            int nx = x ^ (1 << i);
            if (!vt.count(nx)) {
                res.emplace_back(nx);
                vt.emplace(nx);
                dfs(n, nx);
            }
        }
    }
    
    vector<int> grayCode(int n) {
        int start = 0;
        res.emplace_back(start);
        vt.emplace(start);
        dfs(n , start);
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/gray-code/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/gray-code/description/)

Solution: [LeetCode](https://leetcode.com/articles/gray-code/)  /  [LeetCode中国](https://leetcode-cn.com/articles/gray-code/)