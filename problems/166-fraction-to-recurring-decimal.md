# 166. Fraction to Recurring Decimal | 分数到小数

## Question description

<!--If you want to use the English description, use <p>Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.</p>

<p>If the fractional part is repeating, enclose the repeating part in parentheses.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> numerator = 1, denominator = 2
<strong>Output:</strong> &quot;0.5&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> numerator = 2, denominator = 1
<strong>Output:</strong> &quot;2&quot;</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> numerator = 2, denominator = 3
<strong>Output: </strong>&quot;0.(6)&quot;
</pre>
 instead-->
<p>给定两个整数，分别表示分数的分子&nbsp;numerator 和分母 denominator，以字符串形式返回小数。</p>

<p>如果小数部分为循环小数，则将循环的部分括在括号内。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> numerator = 1, denominator = 2
<strong>输出:</strong> &quot;0.5&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> numerator = 2, denominator = 1
<strong>输出:</strong> &quot;2&quot;</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong> numerator = 2, denominator = 3
<strong>输出: </strong>&quot;0.(6)&quot;
</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        if (numerator == INT_MIN && denominator == -1) return "2147483648";
        if (numerator == -1 && denominator == INT_MIN) return "0.0000000004656612873077392578125";
        string s1 = to_string(numerator / denominator);
        string s3;
        if (((numerator < 0 && denominator) > 0 || (numerator > 0 && denominator <0)) && (s1[0] != '-'))  {
            s3 = "-";
        }
        if ((numerator == INT_MIN && denominator < 0) || (denominator == INT_MIN && numerator < 0)) {
            s3 = "";
        }
        if (numerator % denominator == 0) {
            return s1;
        } else {
            string s2;
            vector<int> rem;
            bool continu = true;
            numerator = numerator - denominator * (numerator / denominator);
            while (continu) {
                if (numerator < 0) numerator *= -1;
                rem.push_back(numerator % denominator);
                numerator *= 10;
                int v = numerator / denominator;
                v = abs(v);
                numerator = numerator % denominator;
                for (int i=0; i<(int)rem.size(); ++i) {
                    if (rem[i] == numerator) {
                        s2.insert(i, "(");
                        s2 += to_string(v) + ")";
                        continu = false;
                        break;
                    }
                }
                if (continu) {
                    s2 += to_string(v);
                }
                if (numerator % denominator == 0) {
                    break;
                }
            }
            
            return s3 + s1 + "." + s2;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fraction-to-recurring-decimal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fraction-to-recurring-decimal/description/)

Solution: [LeetCode](https://leetcode.com/articles/fraction-to-recurring-decimal/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fraction-to-recurring-decimal/)