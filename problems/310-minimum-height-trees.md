# 310. Minimum Height Trees | 最小高度树

## Question description

<!--If you want to use the English description, use <p>For an undirected graph with tree characteristics, we can choose any node as the root. The result graph is then a rooted tree. Among all possible rooted trees, those with minimum height are called minimum height trees (MHTs). Given such a graph, write a function to find all the MHTs and return a list of their root labels.</p>

<p><b>Format</b><br />
The graph contains <code>n</code> nodes which are labeled from <code>0</code> to <code>n - 1</code>. You will be given the number <code>n</code> and a list of undirected <code>edges</code> (each edge is a pair of labels).</p>

<p>You can assume that no duplicate edges will appear in <code>edges</code>. Since all edges are undirected, <code>[0, 1]</code> is the same as <code>[1, 0]</code> and thus will not appear together in <code>edges</code>.</p>

<p><b>Example 1 :</b></p>

<pre>
<strong>Input:</strong> <code>n = 4</code>, <code>edges = [[1, 0], [1, 2], [1, 3]]</code>

        0
        |
        1
       / \
      2   3 

<strong>Output:</strong> <code>[1]</code>
</pre>

<p><b>Example 2 :</b></p>

<pre>
<strong>Input:</strong> <code>n = 6</code>, <code>edges = [[0, 3], [1, 3], [2, 3], [4, 3], [5, 4]]</code>

     0  1  2
      \ | /
        3
        |
        4
        |
        5 

<strong>Output:</strong> <code>[3, 4]</code></pre>

<p><b>Note</b>:</p>

<ul>
	<li>According to the <a href="https://en.wikipedia.org/wiki/Tree_(graph_theory)" target="_blank">definition of tree on Wikipedia</a>: &ldquo;a tree is an undirected graph in which any two vertices are connected by <i>exactly</i> one path. In other words, any connected graph without simple cycles is a tree.&rdquo;</li>
	<li>The height of a rooted tree is the number of edges on the longest downward path between the root and a leaf.</li>
</ul>
 instead-->
<p>对于一个具有树特征的无向图，我们可选择任何一个节点作为根。图因此可以成为树，在所有可能的树中，具有最小高度的树被称为最小高度树。给出这样的一个图，写出一个函数找到所有的最小高度树并返回他们的根节点。</p>

<p><strong>格式</strong></p>

<p>该图包含&nbsp;<code>n</code>&nbsp;个节点，标记为&nbsp;<code>0</code>&nbsp;到&nbsp;<code>n - 1</code>。给定数字&nbsp;<code>n</code>&nbsp;和一个无向边&nbsp;<code>edges</code>&nbsp;列表（每一个边都是一对标签）。</p>

<p>你可以假设没有重复的边会出现在&nbsp;<code>edges</code>&nbsp;中。由于所有的边都是无向边， <code>[0, 1]</code>和&nbsp;<code>[1, 0]</code>&nbsp;是相同的，因此不会同时出现在&nbsp;<code>edges</code>&nbsp;里。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>n = 4</code>, <code>edges = [[1, 0], [1, 2], [1, 3]]</code>

        0
        |
        1
       / \
      2   3 

<strong>输出:</strong> <code>[1]</code>
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <code>n = 6</code>, <code>edges = [[0, 3], [1, 3], [2, 3], [4, 3], [5, 4]]</code>

     0  1  2
      \ | /
        3
        |
        4
        |
        5 

<strong>输出:</strong> <code>[3, 4]</code></pre>

<p><strong>说明</strong>:</p>

<ul>
	<li>&nbsp;根据<a href="https://baike.baidu.com/item/%E6%A0%91/2699484?fromtitle=%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84+%E6%A0%91&amp;fromid=12062173&amp;fr=aladdin" target="_blank">树的定义</a>，树是一个无向图，其中任何两个顶点只通过一条路径连接。 换句话说，一个任何没有简单环路的连通图都是一棵树。</li>
	<li>树的高度是指根节点和叶子节点之间最长向下路径上边的数量。</li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 56 ms

```cpp
// refer: https://www.youtube.com/watch?v=4_kTnU05118
class Solution {
public:
    vector<int> findMinHeightTrees(int n, vector<pair<int, int>>& edges) {
        // corner cases
        if (n == 0) {
            return vector<int>();
        } else if (n == 1) {
            return vector<int>{0};
        } else {
            // record each node's degree
            vector<int> degree(n, 0);
            // record nodes connected with current node, or calls connection info
            unordered_map<int, unordered_set<int> > nodes;
            for (auto edge : edges) {
                degree[edge.first]++;
                degree[edge.second]++;
                nodes[edge.first].insert(edge.second);
                nodes[edge.second].insert(edge.first);
            }

            // find out leaf nodes (degree is 1)
            vector<int> leaf;
            for (int i = 0; i < n; ++i) {
                if (degree[i] == 1) {
                    leaf.push_back(i);
                }
            }

            vector<int> tmp;
            while (n > 2) {
                int m = leaf.size();
                n -= m;
                tmp.clear();
                for (int i = 0; i < m; ++i) {
                    // for each leaf node, set its degree to 0
                    int cur = leaf.back();
                    leaf.pop_back();
                    degree[cur] = 0;
                    // for each node connected with the leaf node, decrease its degree by 1
                    // remove current leaf node from the connection info set
                    // then check the degree of the node, if it is 1, push it into leaf list
                    for (int neighbor : nodes[cur]) {
                        degree[neighbor]--;
                        nodes[neighbor].erase(cur);
                        if (degree[neighbor] == 1) {
                            tmp.push_back(neighbor);
                        }
                    }
                }
                leaf = tmp;
            }
            return leaf;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-height-trees/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-height-trees/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-height-trees/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-height-trees/)