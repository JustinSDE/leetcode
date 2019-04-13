# 1002. Find Common Characters | 查找常用字符

## Question description

<!--If you want to use the English description, use <p>Given an array&nbsp;<code>A</code> of strings made only from lowercase letters, return a list of all characters that show up in all strings within the list <strong>(including duplicates)</strong>.&nbsp;&nbsp;For example, if a character occurs 3 times&nbsp;in all strings but not 4 times, you need to include that character three times&nbsp;in the final answer.</p>

<p>You may return the answer in any order.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[&quot;bella&quot;,&quot;label&quot;,&quot;roller&quot;]</span>
<strong>Output: </strong><span id="example-output-1">[&quot;e&quot;,&quot;l&quot;,&quot;l&quot;]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[&quot;cool&quot;,&quot;lock&quot;,&quot;cook&quot;]</span>
<strong>Output: </strong><span id="example-output-2">[&quot;c&quot;,&quot;o&quot;]</span>
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 100</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 100</code></li>
	<li><code>A[i][j]</code> is a lowercase letter</li>
</ol>
</div>
</div> instead-->
<p>给定仅有小写字母组成的字符串数组 <code>A</code>，返回列表中的每个字符串中都显示的全部字符（<strong>包括重复字符</strong>）组成的列表。例如，如果一个字符在每个字符串中出现 3 次，但不是 4 次，则需要在最终答案中包含该字符 3 次。</p>

<p>你可以按任意顺序返回答案。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[&quot;bella&quot;,&quot;label&quot;,&quot;roller&quot;]
<strong>输出：</strong>[&quot;e&quot;,&quot;l&quot;,&quot;l&quot;]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[&quot;cool&quot;,&quot;lock&quot;,&quot;cook&quot;]
<strong>输出：</strong>[&quot;c&quot;,&quot;o&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 100</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 100</code></li>
	<li><code>A[i][j]</code> 是小写字母</li>
</ol>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public List<String> commonChars(String[] A) {
        int[][] rec = new int[26][A.length];
        for (int i = 0; i < A.length; i++) {
            for (int j = 0; j < A[i].length(); j++) {
                rec[A[i].charAt(j) - 'a'][i]++;
            }
        }
        List<String> res = new ArrayList<>();
        for (int i = 0; i < 26; i++) {
            Arrays.sort(rec[i]);
            int j = rec[i][0];
            for (int k = 0; k < j; k++) {
                res.add(new Character((char)('a' + i)).toString());
            }
        }
        return res;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-common-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-common-characters/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-common-characters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-common-characters/)