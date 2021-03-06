# 97. Interleaving String | 交错字符串

## Question description

<!--If you want to use the English description, use <p>Given <em>s1</em>, <em>s2</em>, <em>s3</em>, find whether <em>s3</em> is formed by the interleaving of <em>s1</em> and <em>s2</em>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbcbcac&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbbaccc&quot;
<strong>Output:</strong> false
</pre>
 instead-->
<p>给定三个字符串&nbsp;<em>s1</em>, <em>s2</em>, <em>s3</em>, 验证&nbsp;<em>s3</em>&nbsp;是否是由&nbsp;<em>s1</em>&nbsp;和&nbsp;<em>s2 </em>交错组成的。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbcbcac&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbbaccc&quot;
<strong>输出:</strong> false</pre>




## Solution

Language: **cpp**  /  Runtime: 1868 ms

```cpp
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    void backTracking(string& s1, string& s2, string& s3, int i1, int i2, int i3, int& ret) {
        // cout << "[In] " << i1 << ", " << i2 << ", " << i3 << endl;
        if (ret != -1) {
            return;
        }
        if (i3 == (int)s3.size()) {
            ret = (i1 == (int)s1.size()) && (i2 == (int)s2.size());
            return;
        }
        if (i1 < (int)s1.size() && s3[i3] == s1[i1]) {
            i1++;
            i3++;
            backTracking(s1, s2, s3, i1, i2, i3, ret);
            i1--;
            i3--;
        }
        if (i2 < (int)s2.size() && s3[i3] == s2[i2]) {
            i2++;
            i3++;
            backTracking(s1, s2, s3, i1, i2, i3, ret);
            i2--;
            i3--;
        }
        // cout << "[Out] " << i1 << ", " << i2 << ", " << i3 << endl;
    }

    bool isInterleave(string s1, string s2, string s3) {
        int ret = -1;
        backTracking(s1, s2, s3, 0, 0, 0, ret);
        // cout << "ret: " << ret << endl;
        return ret == 1;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/interleaving-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/interleaving-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/interleaving-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/interleaving-string/)