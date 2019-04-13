# 947. Most Stones Removed with Same Row or Column | 移除最多的同行或同列石头

## Question description

<!--If you want to use the English description, use <p>On a 2D plane, we place stones at some integer coordinate points.&nbsp; Each coordinate point may have at most one stone.</p>

<p>Now, a <em>move</em> consists of removing a stone&nbsp;that shares a column or row with another stone on the grid.</p>

<p>What is the largest possible number of moves we can make?</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>stones = <span id="example-input-1-2">[[0,0],[0,1],[1,0],[1,2],[2,1],[2,2]]</span>
<strong>Output: </strong>5
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>stones = <span id="example-input-2-2">[[0,0],[0,2],[1,1],[2,0],[2,2]]</span>
<strong>Output: </strong>3
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>stones = <span id="example-input-3-2">[[0,0]]</span>
<strong>Output: </strong>0
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>1 &lt;= stones.length &lt;= 1000</code></li>
	<li><code>0 &lt;= stones[i][j] &lt; 10000</code></li>
</ol>
</div>
</div>
</div>
 instead-->
<p>在二维平面上，我们将石头放置在一些整数坐标点上。每个坐标点上最多只能有一块石头。<br>
<br>
现在，<em>move</em> 操作将会移除与网格上的某一块石头共享一列或一行的一块石头。<br>
<br>
我们最多能执行多少次 <em>move</em> 操作？</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>stones = [[0,0],[0,1],[1,0],[1,2],[2,1],[2,2]]
<strong>输出：</strong>5
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>stones = [[0,0],[0,2],[1,1],[2,0],[2,2]]
<strong>输出：</strong>3
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>stones = [[0,0]]
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= stones.length &lt;= 1000</code></li>
	<li><code>0 &lt;= stones[i][j] &lt; 10000</code></li>
</ol>


## Note

![image](https://user-images.githubusercontent.com/9983385/54690697-ea361c80-4b5c-11e9-9bd9-a97cb5737aa8.png)




## Solution

Language: **cpp**  /  Runtime: 44 ms

```cpp
class UF {
public:
    vector<int> pre;
    UF(int n) {
        for (int i = 0; i < n; i++)
            pre.push_back(i);
    }
    
    int find(int x) {
        return pre[x] == x ? x : pre[x] = find(pre[x]);
    }
    
    void join(int x, int y) {
        int xr = find(x);
        int yr = find(y);
        if (xr != yr) {
            pre[xr] = yr;
        }
    }
    
    bool connected(int x, int y) {
        return find(x) == find(y);
    }
};

class Solution {
public:
    int removeStones(vector<vector<int>>& stones) {
        int n = stones.size();
        UF uf(20000);
        for (auto s : stones) {
            uf.join(s[0], s[1] + 10000);
        }
        unordered_set<int> conn;
        for (auto s : stones) {
            conn.insert(uf.find(s[0]));
        }
        return stones.size() - conn.size();
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/most-stones-removed-with-same-row-or-column/description/)

Solution: [LeetCode](https://leetcode.com/articles/most-stones-removed-with-same-row-or-column/)  /  [LeetCode中国](https://leetcode-cn.com/articles/most-stones-removed-with-same-row-or-column/)