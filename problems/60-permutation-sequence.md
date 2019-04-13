# 60. Permutation Sequence | 第k个排列

## Question description

<!--If you want to use the English description, use <p>The set <code>[1,2,3,...,<em>n</em>]</code> contains a total of <em>n</em>! unique permutations.</p>

<p>By listing and labeling all of the permutations in order, we get the following sequence for <em>n</em> = 3:</p>

<ol>
	<li><code>&quot;123&quot;</code></li>
	<li><code>&quot;132&quot;</code></li>
	<li><code>&quot;213&quot;</code></li>
	<li><code>&quot;231&quot;</code></li>
	<li><code>&quot;312&quot;</code></li>
	<li><code>&quot;321&quot;</code></li>
</ol>

<p>Given <em>n</em> and <em>k</em>, return the <em>k</em><sup>th</sup> permutation sequence.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>Given <em>n</em> will be between 1 and 9 inclusive.</li>
	<li>Given&nbsp;<em>k</em>&nbsp;will be between 1 and <em>n</em>! inclusive.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3, k = 3
<strong>Output:</strong> &quot;213&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 4, k = 9
<strong>Output:</strong> &quot;2314&quot;
</pre>
 instead-->
<p>给出集合&nbsp;<code>[1,2,3,&hellip;,<em>n</em>]</code>，其所有元素共有&nbsp;<em>n</em>! 种排列。</p>

<p>按大小顺序列出所有排列情况，并一一标记，当&nbsp;<em>n </em>= 3 时, 所有排列如下：</p>

<ol>
	<li><code>&quot;123&quot;</code></li>
	<li><code>&quot;132&quot;</code></li>
	<li><code>&quot;213&quot;</code></li>
	<li><code>&quot;231&quot;</code></li>
	<li><code>&quot;312&quot;</code></li>
	<li><code>&quot;321&quot;</code></li>
</ol>

<p>给定&nbsp;<em>n</em> 和&nbsp;<em>k</em>，返回第&nbsp;<em>k</em>&nbsp;个排列。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>给定<em> n</em>&nbsp;的范围是 [1, 9]。</li>
	<li>给定 <em>k&nbsp;</em>的范围是[1, &nbsp;<em>n</em>!]。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> n = 3, k = 3
<strong>输出:</strong> &quot;213&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> n = 4, k = 9
<strong>输出:</strong> &quot;2314&quot;
</pre>


## Note

直接用Python自带的`itertools.permutations`枚举所有组合并缓存在类属性里，很暴力地AC了，当然时间复杂度也高。


## Solution

Language: **python3**  /  Runtime: 164 ms

```python3
import itertools
class Solution:
    cache = {}
    def getPermutation(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: str
        """
        if n not in __class__.cache:
            __class__.cache[n] = list(itertools.permutations(range(1, n+1)))
        return ''.join(map(str, __class__.cache[n][k-1]))

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/permutation-sequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/permutation-sequence/description/)

Solution: [LeetCode](https://leetcode.com/articles/permutation-sequence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/permutation-sequence/)