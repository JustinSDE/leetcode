# 395. Longest Substring with At Least K Repeating Characters | 至少有K个重复字符的最长子串

## Question description

<!--If you want to use the English description, use <p>
Find the length of the longest substring <b><i>T</i></b> of a given string (consists of lowercase letters only) such that every character in <b><i>T</i></b> appears no less than <i>k</i> times.
</p>

<p><b>Example 1:</b>
<pre>
Input:
s = "aaabb", k = 3

Output:
3

The longest substring is "aaa", as 'a' is repeated 3 times.
</pre>
</p>

<p><b>Example 2:</b>
<pre>
Input:
s = "ababbc", k = 2

Output:
5

The longest substring is "ababb", as 'a' is repeated 2 times and 'b' is repeated 3 times.
</pre>
</p> instead-->
<p>找到给定字符串（由小写字符组成）中的最长子串 <strong><em>T</em></strong> ，&nbsp;要求&nbsp;<strong><em>T</em></strong>&nbsp;中的每一字符出现次数都不少于 <em>k</em> 。输出 <strong><em>T&nbsp;</em></strong>的长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
输入:
s = &quot;aaabb&quot;, k = 3

输出:
3

最长子串为 &quot;aaa&quot; ，其中 &#39;a&#39; 重复了 3 次。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
输入:
s = &quot;ababbc&quot;, k = 2

输出:
5

最长子串为 &quot;ababb&quot; ，其中 &#39;a&#39; 重复了 2 次， &#39;b&#39; 重复了 3 次。
</pre>


## Note

![TIM图片20190410160019](https://user-images.githubusercontent.com/9983385/55861834-d012bb80-5ba9-11e9-98db-1e5c735ac2c6.jpg)


## Solution

Language: **java**  /  Runtime: 11 ms

```java
class Solution {
    public int longestSubstring(String s, int k) {
        if (s.length() == 0 || s.length() < k) return 0;
        int res = 0;
        HashMap<Character, Integer> map = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            map.put(s.charAt(i), map.getOrDefault(s.charAt(i), 0) + 1);
        }
        StringBuilder sb = new StringBuilder();
        for (HashMap.Entry<Character, Integer> kv : map.entrySet()) {
            if (kv.getValue() < k) {
                sb.append(kv.getKey());
            }
        }
        if (sb.length() == 0) {
            return s.length();
        } else {
            sb.insert(0, '[');
            sb.append(']');
        }
        String[] ss = s.split(sb.toString());
        for (String si : ss) {
            res = Math.max(res, longestSubstring(si, k));
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-substring-with-at-least-k-repeating-characters/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-substring-with-at-least-k-repeating-characters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-substring-with-at-least-k-repeating-characters/)