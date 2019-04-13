# 385. Mini Parser | 迷你语法分析器

## Question description

<!--If you want to use the English description, use <p>Given a nested list of integers represented as a string, implement a parser to deserialize it.</p>

<p>Each element is either an integer, or a list -- whose elements may also be integers or other lists.</p>

<p><b>Note:</b>
You may assume that the string is well-formed:
<ul>
<li>String is non-empty.</li>
<li>String does not contain white spaces.</li>
<li>String contains only digits <code>0-9</code>, <code>[</code>, <code>-</code> <code>,</code>, <code>]</code>.</li>
</ul>
</p>

<p><b>Example 1:</b>
<pre>
Given s = "324",

You should return a NestedInteger object which contains a single integer 324.
</pre>
</p>

<p><b>Example 2:</b>
<pre>
Given s = "[123,[456,[789]]]",

Return a NestedInteger object containing a nested list with 2 elements:

1. An integer containing value 123.
2. A nested list containing two elements:
    i.  An integer containing value 456.
    ii. A nested list with one element:
         a. An integer containing value 789.
</pre>
</p> instead-->
<p>给定一个用字符串表示的整数的嵌套列表，实现一个解析它的语法分析器。</p>

<p>列表中的每个元素只可能是整数或整数嵌套列表</p>

<p><strong>提示：</strong>你可以假定这些字符串都是格式良好的：</p>

<ul>
	<li>字符串非空</li>
	<li>字符串不包含空格</li>
	<li>字符串只包含数字<code>0-9</code>, <code>[</code>, <code>-</code> <code>,</code>, <code>]</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
给定 s = &quot;324&quot;,

你应该返回一个 NestedInteger 对象，其中只包含整数值 324。
</pre>

<p>&nbsp;</p>

<p><strong>示例 2：</strong></p>

<pre>
给定 s = &quot;[123,[456,[789]]]&quot;,

返回一个 NestedInteger 对象包含一个有两个元素的嵌套列表：

1. 一个 integer 包含值 123
2. 一个包含两个元素的嵌套列表：
    i.  一个 integer 包含值 456
    ii. 一个包含一个元素的嵌套列表
         a. 一个 integer 包含值 789
</pre>

<p>&nbsp;</p>




## Solution

Language: **cpp**  /  Runtime: 16 ms

```cpp
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * class NestedInteger {
 *   public:
 *     // Constructor initializes an empty nested list.
 *     NestedInteger();
 *
 *     // Constructor initializes a single integer.
 *     NestedInteger(int value);
 *
 *     // Return true if this NestedInteger holds a single integer, rather than a nested list.
 *     bool isInteger() const;
 *
 *     // Return the single integer that this NestedInteger holds, if it holds a single integer
 *     // The result is undefined if this NestedInteger holds a nested list
 *     int getInteger() const;
 *
 *     // Set this NestedInteger to hold a single integer.
 *     void setInteger(int value);
 *
 *     // Set this NestedInteger to hold a nested list and adds a nested integer to it.
 *     void add(const NestedInteger &ni);
 *
 *     // Return the nested list that this NestedInteger holds, if it holds a nested list
 *     // The result is undefined if this NestedInteger holds a single integer
 *     const vector<NestedInteger> &getList() const;
 * };
 */
class Solution {
public:
    NestedInteger deserialize(string s) {
        if (s[0] != '[') {
            NestedInteger res(stoi(s));
            return res;
        } else {
            stack<NestedInteger> stk;
            for (int i = 0; i < s.size() - 1; ) {
                if (s[i] == '[') {
                    NestedInteger tmp;
                    stk.push(tmp);
                    i++;
                } else if (s[i] == ']') {
                    NestedInteger tmp = stk.top();
                    stk.pop();
                    stk.top().add(tmp);
                    i++;
                } else if (s[i] == ',') {
                    i++;
                } else {
                    int j = i;
                    // Note: for (init; continue; step)
                    for (; isdigit(s[i]) || s[i] == '-'; ++i) ;
                    stk.top().add(stoi(s.substr(j, i - j)));
                }
            }
            return stk.top();
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/mini-parser/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/mini-parser/description/)

Solution: [LeetCode](https://leetcode.com/articles/mini-parser/)  /  [LeetCode中国](https://leetcode-cn.com/articles/mini-parser/)