# 187. Repeated DNA Sequences | 重复的DNA序列

## Question description

<!--If you want to use the English description, use <p>All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: &quot;ACGAATTCCG&quot;. When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.</p>

<p>Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT&quot;

<strong>Output:</strong> [&quot;AAAAACCCCC&quot;, &quot;CCCCCAAAAA&quot;]
</pre>
 instead-->
<p>所有 DNA 由一系列缩写为 A，C，G 和 T 的核苷酸组成，例如：&ldquo;ACGAATTCCG&rdquo;。在研究 DNA 时，识别 DNA 中的重复序列有时会对研究非常有帮助。</p>

<p>编写一个函数来查找 DNA 分子中所有出现超多一次的10个字母长的序列（子串）。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> s = &quot;AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT&quot;

<strong>输出:</strong> [&quot;AAAAACCCCC&quot;, &quot;CCCCCAAAAA&quot;]</pre>




## Solution

Language: **cpp**  /  Runtime: 40 ms

```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        vector<string> res;
        if (s.size() < 10) return res;
        unordered_map<string, int> M;
        for (int i=0; i<=s.size()-10; ++i) {
            M[s.substr(i, 10)]++;
        }
        for (auto m : M) {
            if (m.second > 1) {
                res.push_back(m.first);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/repeated-dna-sequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/repeated-dna-sequences/description/)

Solution: [LeetCode](https://leetcode.com/articles/repeated-dna-sequences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/repeated-dna-sequences/)