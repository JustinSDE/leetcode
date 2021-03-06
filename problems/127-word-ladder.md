# 127. Word Ladder | 单词接龙

## Question description

<!--If you want to use the English description, use <p>Given two words (<em>beginWord</em> and <em>endWord</em>), and a dictionary&#39;s word list, find the length of shortest transformation sequence from <em>beginWord</em> to <em>endWord</em>, such that:</p>

<ol>
	<li>Only one letter can be changed at a time.</li>
	<li>Each transformed word must exist in the word list. Note that <em>beginWord</em> is <em>not</em> a transformed word.</li>
</ol>

<p><strong>Note:</strong></p>

<ul>
	<li>Return 0 if there is no such transformation sequence.</li>
	<li>All words have the same length.</li>
	<li>All words contain only lowercase alphabetic characters.</li>
	<li>You may assume no duplicates in the word list.</li>
	<li>You may assume <em>beginWord</em> and <em>endWord</em> are non-empty and are not the same.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
beginWord = &quot;hit&quot;,
endWord = &quot;cog&quot;,
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;,&quot;cog&quot;]

<strong>Output: </strong>5

<strong>Explanation:</strong> As one shortest transformation is &quot;hit&quot; -&gt; &quot;hot&quot; -&gt; &quot;dot&quot; -&gt; &quot;dog&quot; -&gt; &quot;cog&quot;,
return its length 5.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>
beginWord = &quot;hit&quot;
endWord = &quot;cog&quot;
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;]

<strong>Output:</strong>&nbsp;0

<strong>Explanation:</strong>&nbsp;The endWord &quot;cog&quot; is not in wordList, therefore no possible<strong>&nbsp;</strong>transformation.
</pre>

<ul>
</ul>
 instead-->
<p>给定两个单词（<em>beginWord&nbsp;</em>和 <em>endWord</em>）和一个字典，找到从&nbsp;<em>beginWord</em> 到&nbsp;<em>endWord</em> 的最短转换序列的长度。转换需遵循如下规则：</p>

<ol>
	<li>每次转换只能改变一个字母。</li>
	<li>转换过程中的中间单词必须是字典中的单词。</li>
</ol>

<p><strong>说明:</strong></p>

<ul>
	<li>如果不存在这样的转换序列，返回 0。</li>
	<li>所有单词具有相同的长度。</li>
	<li>所有单词只由小写字母组成。</li>
	<li>字典中不存在重复的单词。</li>
	<li>你可以假设 <em>beginWord</em> 和 <em>endWord </em>是非空的，且二者不相同。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
beginWord = &quot;hit&quot;,
endWord = &quot;cog&quot;,
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;,&quot;cog&quot;]

<strong>输出: </strong>5

<strong>解释: </strong>一个最短转换序列是 &quot;hit&quot; -&gt; &quot;hot&quot; -&gt; &quot;dot&quot; -&gt; &quot;dog&quot; -&gt; &quot;cog&quot;,
     返回它的长度 5。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
beginWord = &quot;hit&quot;
endWord = &quot;cog&quot;
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;]

<strong>输出:</strong>&nbsp;0

<strong>解释:</strong>&nbsp;<em>endWord</em> &quot;cog&quot; 不在字典中，所以无法进行转换。</pre>




## Solution

Language: **cpp**  /  Runtime: 340 ms

```cpp
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    bool diffone(string& s1, string& s2) {
        int res = 0;
        for (int i=0; i<(int)s1.size(); ++i) {
            if (s1[i] != s2[i]) {
                if (1 < ++res) {
                    return false;
                }
            }
        }
        return res == 1;
    }
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        queue<string> Q;
        unordered_set<string> avail;
        avail.insert(wordList.begin(), wordList.end());
        int res = 0;
        Q.push(beginWord);
        avail.erase(beginWord);
        vector<string> del;
        while (!Q.empty()) {
            int n = Q.size();
            res++;
            while (n--) {
                string tmp = Q.front();
                Q.pop();
                del.clear();
                for (auto s : avail) {
                    if (diffone(s, tmp)) {
                        if (s == endWord) {
                            return res + 1;
                        }
                        Q.push(s);
                        del.push_back(s);
                    }
                }
                for (auto s : del) {
                    avail.erase(s);
                }
            }
        }
        return 0;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/word-ladder/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-ladder/description/)

Solution: [LeetCode](https://leetcode.com/articles/word-ladder/)  /  [LeetCode中国](https://leetcode-cn.com/articles/word-ladder/)