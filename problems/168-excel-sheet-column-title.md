# 168. Excel Sheet Column Title | Excel表列名称

## Question description

<!--If you want to use the English description, use <p>Given a positive integer, return its corresponding column title as appear in an Excel sheet.</p>

<p>For example:</p>

<pre>
    1 -&gt; A
    2 -&gt; B
    3 -&gt; C
    ...
    26 -&gt; Z
    27 -&gt; AA
    28 -&gt; AB 
    ...
</pre>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1
<strong>Output:</strong> &quot;A&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 28
<strong>Output:</strong> &quot;AB&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 701
<strong>Output:</strong> &quot;ZY&quot;
</pre> instead-->
<p>给定一个正整数，返回它在 Excel 表中相对应的列名称。</p>

<p>例如，</p>

<pre>    1 -&gt; A
    2 -&gt; B
    3 -&gt; C
    ...
    26 -&gt; Z
    27 -&gt; AA
    28 -&gt; AB 
    ...
</pre>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 1
<strong>输出:</strong> &quot;A&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 28
<strong>输出:</strong> &quot;AB&quot;
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong> 701
<strong>输出:</strong> &quot;ZY&quot;
</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public String convertToTitle(int n) {
        StringBuilder sb = new StringBuilder();
        String s = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        while (n > 0) {
            sb.append(s.charAt((n - 1) % 26));
            n = (n - 1) / 26;
        }
        return sb.reverse().toString();
    }
}
```

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    string convertToTitle(int n) {
        string alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        string res;
        /*
        A-Z  1-26
        AA 27 26+1  26*1+1
        AB 28 26+2  26*1+2
        AZ    26*1+26
        BA    26*2+1
        BB    26*2+2
        ZY    26*26+25
        ZZ    26*26+26
        AAA   26*26*1+26*1+1
        */
        while (n) {
            if (n % 26 == 0) {
                res = 'Z' + res;
                n = n / 26 - 1;
            } else {
                res = alphabet[n % 26 - 1] + res;
                n /= 26;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/excel-sheet-column-title/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/excel-sheet-column-title/description/)

Solution: [LeetCode](https://leetcode.com/articles/excel-sheet-column-title/)  /  [LeetCode中国](https://leetcode-cn.com/articles/excel-sheet-column-title/)