# 970. Powerful Integers | 强整数

## Question description

<!--If you want to use the English description, use <p>Given two positive integers <code>x</code> and <code>y</code>, an integer is <em>powerful</em>&nbsp;if it is equal to <code>x^i + y^j</code>&nbsp;for&nbsp;some integers <code>i &gt;= 0</code> and <code>j &gt;= 0</code>.</p>

<p>Return a list of all <em>powerful</em> integers that have value less than or equal to <code>bound</code>.</p>

<p>You may return the answer in any order.&nbsp; In your answer, each value should occur at most once.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>x = <span id="example-input-1-1">2</span>, y = <span id="example-input-1-2">3</span>, bound = <span id="example-input-1-3">10</span>
<strong>Output: </strong><span id="example-output-1">[2,3,4,5,7,9,10]</span>
<strong>Explanation: </strong>
2 = 2^0 + 3^0
3 = 2^1 + 3^0
4 = 2^0 + 3^1
5 = 2^1 + 3^1
7 = 2^2 + 3^1
9 = 2^3 + 3^0
10 = 2^0 + 3^2
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>x = <span id="example-input-2-1">3</span>, y = <span id="example-input-2-2">5</span>, bound = <span id="example-input-2-3">15</span>
<strong>Output: </strong><span id="example-output-2">[2,4,6,8,10,14]</span>
</pre>
</div>
</div>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li><code>1 &lt;= x &lt;= 100</code></li>
	<li><code>1 &lt;= y&nbsp;&lt;= 100</code></li>
	<li><code>0 &lt;= bound&nbsp;&lt;= 10^6</code></li>
</ul> instead-->
<p>给定两个正整数 <code>x</code> 和 <code>y</code>，如果某一整数等于 <code>x^i + y^j</code>，其中整数&nbsp;<code>i &gt;= 0</code> 且&nbsp;<code>j &gt;= 0</code>，那么我们认为该整数是一个<em>强整数</em>。</p>

<p>返回值小于或等于&nbsp;<code>bound</code>&nbsp;的所有<em>强整数</em>组成的列表。</p>

<p>你可以按任何顺序返回答案。在你的回答中，每个值最多出现一次。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>x = 2, y = 3, bound = 10
<strong>输出：</strong>[2,3,4,5,7,9,10]
<strong>解释： </strong>
2 = 2^0 + 3^0
3 = 2^1 + 3^0
4 = 2^0 + 3^1
5 = 2^1 + 3^1
7 = 2^2 + 3^1
9 = 2^3 + 3^0
10 = 2^0 + 3^2
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>x = 3, y = 5, bound = 15
<strong>输出：</strong>[2,4,6,8,10,14]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= x &lt;= 100</code></li>
	<li><code>1 &lt;= y&nbsp;&lt;= 100</code></li>
	<li><code>0 &lt;= bound&nbsp;&lt;= 10^6</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 8 ms

```cpp
class Solution {
public:
    vector<int> powerfulIntegers(int x, int y, int bound) {
        set<int> us;
        for (int i=0; x==1 ? i<1 : pow(x, i) < bound; ++i) {
            for (int j=0; y==1 ? j<1 : pow(y, j) < bound; ++j) {
                int z = pow(x, i) + pow(y, j);
                if (z <= bound) {
                    us.insert(z);
                }
            }
        }
        vector<int> res;
        for (int i : us) {
            res.push_back(i);
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/powerful-integers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/powerful-integers/description/)

Solution: [LeetCode](https://leetcode.com/articles/powerful-integers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/powerful-integers/)