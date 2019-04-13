# 10. Regular Expression Matching | 正则表达式匹配

## Question description

<!--If you want to use the English description, use <p>Given an input string (<code>s</code>) and a pattern (<code>p</code>), implement regular expression matching with support for <code>&#39;.&#39;</code> and <code>&#39;*&#39;</code>.</p>

<pre>
&#39;.&#39; Matches any single character.
&#39;*&#39; Matches zero or more of the preceding element.
</pre>

<p>The matching should cover the <strong>entire</strong> input string (not partial).</p>

<p><strong>Note:</strong></p>

<ul>
	<li><code>s</code>&nbsp;could be empty and contains only lowercase letters <code>a-z</code>.</li>
	<li><code>p</code> could be empty and contains only lowercase letters <code>a-z</code>, and characters like&nbsp;<code>.</code>&nbsp;or&nbsp;<code>*</code>.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
s = &quot;aa&quot;
p = &quot;a&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> &quot;a&quot; does not match the entire string &quot;aa&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>
s = &quot;aa&quot;
p = &quot;a*&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>&nbsp;&#39;*&#39; means zero or more of the precedeng&nbsp;element, &#39;a&#39;. Therefore, by repeating &#39;a&#39; once, it becomes &quot;aa&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong>
s = &quot;ab&quot;
p = &quot;.*&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>&nbsp;&quot;.*&quot; means &quot;zero or more (*) of any character (.)&quot;.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong>
s = &quot;aab&quot;
p = &quot;c*a*b&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>&nbsp;c can be repeated 0 times, a can be repeated 1 time. Therefore it matches &quot;aab&quot;.
</pre>

<p><strong>Example 5:</strong></p>

<pre>
<strong>Input:</strong>
s = &quot;mississippi&quot;
p = &quot;mis*is*p*.&quot;
<strong>Output:</strong> false
</pre>
 instead-->
<p>给定一个字符串&nbsp;(<code>s</code>) 和一个字符模式&nbsp;(<code>p</code>)。实现支持 <code>&#39;.&#39;</code>&nbsp;和&nbsp;<code>&#39;*&#39;</code>&nbsp;的正则表达式匹配。</p>

<pre>&#39;.&#39; 匹配任意单个字符。
&#39;*&#39; 匹配零个或多个前面的元素。
</pre>

<p>匹配应该覆盖<strong>整个</strong>字符串&nbsp;(<code>s</code>) ，而不是部分字符串。</p>

<p><strong>说明:</strong></p>

<ul>
	<li><code>s</code>&nbsp;可能为空，且只包含从&nbsp;<code>a-z</code>&nbsp;的小写字母。</li>
	<li><code>p</code>&nbsp;可能为空，且只包含从&nbsp;<code>a-z</code>&nbsp;的小写字母，以及字符&nbsp;<code>.</code>&nbsp;和&nbsp;<code>*</code>。</li>
</ul>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
s = &quot;aa&quot;
p = &quot;a&quot;
<strong>输出:</strong> false
<strong>解释:</strong> &quot;a&quot; 无法匹配 &quot;aa&quot; 整个字符串。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
s = &quot;aa&quot;
p = &quot;a*&quot;
<strong>输出:</strong> true
<strong>解释:</strong>&nbsp;&#39;*&#39; 代表可匹配零个或多个前面的元素, 即可以匹配 &#39;a&#39; 。因此, 重复 &#39;a&#39; 一次, 字符串可变为 &quot;aa&quot;。
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong>
s = &quot;ab&quot;
p = &quot;.*&quot;
<strong>输出:</strong> true
<strong>解释:</strong>&nbsp;&quot;.*&quot; 表示可匹配零个或多个(&#39;*&#39;)任意字符(&#39;.&#39;)。
</pre>

<p><strong>示例 4:</strong></p>

<pre><strong>输入:</strong>
s = &quot;aab&quot;
p = &quot;c*a*b&quot;
<strong>输出:</strong> true
<strong>解释:</strong>&nbsp;&#39;c&#39; 可以不被重复, &#39;a&#39; 可以被重复一次。因此可以匹配字符串 &quot;aab&quot;。
</pre>

<p><strong>示例 5:</strong></p>

<pre><strong>输入:</strong>
s = &quot;mississippi&quot;
p = &quot;mis*is*p*.&quot;
<strong>输出:</strong> false</pre>


## Note

这个似乎是剑指Offer上的题目，意在考查正则表达式的实现。

第一次做这个题目花了好几个小时的时间，没办法，比较菜。

最开始的思路是扫描s和p，结果发现可能性实在太多了，if else嵌套了很多，剪不断理还乱，放弃。

然后想到可以把p解析成 (字符, 最少出现次数, 最大出现次数) ，把s解析成 (字符, 出现次数），然后进行比对，但是这种方案依然存在诸多问题，主要是`*`究竟要匹配多长。

后来想着，能不能通过递归的方式求解，于是，考虑把问题进行分解，终于写成了一版AC的代码。不过，由于存在大量重复计算，耗时较长。


## Solution

Language: **java**  /  Runtime: 55 ms

```java
class Solution {
    public boolean isMatch(String s, String p) {
        if (p.isEmpty()) return s.isEmpty();
        boolean first_match = !s.isEmpty() && (p.charAt(0) == '.' || (s.charAt(0) == p.charAt(0)));
        if (p.length() >= 2 && p.charAt(1) == '*') {
            return isMatch(s, p.substring(2)) || (first_match && isMatch(s.substring(1), p));
        } else {
            return first_match && isMatch(s.substring(1), p.substring(1));
        }
    }
}
/*
"aa"
"a"
"aa"
"a*"
"ab"
".*"
"aab"
"c*a*b"
"mississippi"
"mis*is*p*."
"a"
".*..a*"
*/
```

Language: **cpp**  /  Runtime: 120 ms

```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        // cout << s << ", " << p << endl;
        if(s == p){
            return true;
        }
        if(p.length() == 0){
            return s == "";
        }
        if(p.length() == 1){
            return s.length() == 1 && (p.at(0) == '.' || p.at(0) == s.at(0));
        }
        if(p.length() == 2){
            if(p.at(1) == '*'){
                if(p.at(0) == '.'){  // .*
                    return true;
                }else{  // a*
                    for(char c : s){
                        if(c != p.at(0)){
                            return false;
                        }
                    }
                    return true;
                }
            }else{  // ab
                if(s.length() == 2){
                    return isMatch(s.substr(0, 1), p.substr(0, 1)) && isMatch(s.substr(1, 1), p.substr(1, 1));
                }else{
                    return false;
                }
            }
        }
        if(p.length() > 2){
            if(p.at(1) == '*'){  // a*b   .*b   a*.*b   .*bcd
                size_t i = 0;
                while(i <= s.length()){
                    if(isMatch(s.substr(0, i), p.substr(0, 2)) && isMatch(s.substr(i, s.length()-i), p.substr(2, p.length()-2))){
                        return true;
                    }
                    i++;
                }
                return false;
            }else{  // abc  abcd  abc*  ab.*  b.*  b.*ac
                return (isMatch(s.substr(0, 1), p.substr(0, 1)) && isMatch(s.substr(1, s.length()-1), p.substr(1, p.length()-1))) || (isMatch(s.substr(0, 2), p.substr(0, 2)) && isMatch(s.substr(2, s.length()-2), p.substr(2, p.length()-2)));
            }
        }
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/regular-expression-matching/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/regular-expression-matching/description/)

Solution: [LeetCode](https://leetcode.com/articles/regular-expression-matching/)  /  [LeetCode中国](https://leetcode-cn.com/articles/regular-expression-matching/)