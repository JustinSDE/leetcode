# 412. Fizz Buzz | Fizz Buzz

## Question description

<!--If you want to use the English description, use <p>Write a program that outputs the string representation of numbers from 1 to <i>n</i>.</p>

<p>But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.</p>

<p><b>Example:</b>
<pre>
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
</pre>
</p> instead-->
<p>写一个程序，输出从 1 到 <em>n</em> 数字的字符串表示。</p>

<p>1. 如果&nbsp;<em>n&nbsp;</em>是3的倍数，输出&ldquo;Fizz&rdquo;；</p>

<p>2. 如果&nbsp;<em>n&nbsp;</em>是5的倍数，输出&ldquo;Buzz&rdquo;；</p>

<p>3.如果&nbsp;<em>n&nbsp;</em>同时是3和5的倍数，输出 &ldquo;FizzBuzz&rdquo;。</p>

<p><strong>示例：</strong></p>

<pre>n = 15,

返回:
[
    &quot;1&quot;,
    &quot;2&quot;,
    &quot;Fizz&quot;,
    &quot;4&quot;,
    &quot;Buzz&quot;,
    &quot;Fizz&quot;,
    &quot;7&quot;,
    &quot;8&quot;,
    &quot;Fizz&quot;,
    &quot;Buzz&quot;,
    &quot;11&quot;,
    &quot;Fizz&quot;,
    &quot;13&quot;,
    &quot;14&quot;,
    &quot;FizzBuzz&quot;
]
</pre>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> res = new ArrayList<>();
        for (int i = 1; i <= n; i++) {
            if (i %  3 == 0 && i % 5 == 0) {
                res.add("FizzBuzz");
            } else {
                if (i % 3 == 0) {
                    res.add("Fizz");
                } else if (i % 5 == 0) {
                    res.add("Buzz");
                } else {
                    res.add(String.valueOf(i));
                }
            }
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/fizz-buzz/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fizz-buzz/description/)

Solution: [LeetCode](https://leetcode.com/articles/fizz-buzz/)  /  [LeetCode中国](https://leetcode-cn.com/articles/fizz-buzz/)