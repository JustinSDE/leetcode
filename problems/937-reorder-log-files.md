# 937. Reorder Log Files | 重新排列日志文件

## Question description

<!--If you want to use the English description, use <p>You have an array of <code>logs</code>.&nbsp; Each log is a space delimited string of words.</p>

<p>For each log, the first word in each log is an alphanumeric <em>identifier</em>.&nbsp; Then, either:</p>

<ul>
	<li>Each word after the identifier will consist only of lowercase letters, or;</li>
	<li>Each word after the identifier will consist only of digits.</li>
</ul>

<p>We will call these two varieties of logs <em>letter-logs</em> and <em>digit-logs</em>.&nbsp; It is guaranteed that each log has at least one word after its identifier.</p>

<p>Reorder the logs so that all of the letter-logs come before any digit-log.&nbsp; The letter-logs are ordered lexicographically ignoring identifier, with the identifier used in case of ties.&nbsp; The digit-logs should be put in their original order.</p>

<p>Return the final order of the logs.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[&quot;a1 9 2 3 1&quot;,&quot;g1 act car&quot;,&quot;zo4 4 7&quot;,&quot;ab1 off key dog&quot;,&quot;a8 act zoo&quot;]</span>
<strong>Output: </strong><span id="example-output-1">[&quot;g1 act car&quot;,&quot;a8 act zoo&quot;,&quot;ab1 off key dog&quot;,&quot;a1 9 2 3 1&quot;,&quot;zo4 4 7&quot;]</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>0 &lt;= logs.length &lt;= 100</code></li>
	<li><code>3 &lt;= logs[i].length &lt;= 100</code></li>
	<li><code>logs[i]</code> is guaranteed to have an identifier, and a word after the identifier.</li>
</ol>
</div> instead-->
<p>你有一个日志数组 <code>logs</code>。每条日志都是以空格分隔的字串。</p>

<p>对于每条日志，其第一个字为字母数字<em>标识符</em>。然后，要么：</p>

<ul>
	<li>标识符后面的每个字将仅由小写字母组成，或；</li>
	<li>标识符后面的每个字将仅由数字组成。</li>
</ul>

<p>我们将这两种日志分别称为字母日志和数字日志。保证每个日志在其标识符后面至少有一个字。</p>

<p>将日志重新排序，使得所有字母日志都排在数字日志之前。字母日志按字母顺序排序，忽略标识符，标识符仅用于表示关系。数字日志应该按原来的顺序排列。</p>

<p>返回日志的最终顺序。</p>

<p>&nbsp;</p>

<p><strong>示例 ：</strong></p>

<pre><strong>输入：</strong>[&quot;a1 9 2 3 1&quot;,&quot;g1 act car&quot;,&quot;zo4 4 7&quot;,&quot;ab1 off key dog&quot;,&quot;a8 act zoo&quot;]
<strong>输出：</strong>[&quot;g1 act car&quot;,&quot;a8 act zoo&quot;,&quot;ab1 off key dog&quot;,&quot;a1 9 2 3 1&quot;,&quot;zo4 4 7&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= logs.length &lt;= 100</code></li>
	<li><code>3 &lt;= logs[i].length &lt;= 100</code></li>
	<li><code>logs[i]</code>&nbsp;保证有一个标识符，并且标识符后面有一个字。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:
        return sorted(list(filter(lambda l : l[l.index(' ') + 1].isalpha(), logs)), key=lambda x : x[x.index(' '):]) + list(filter(lambda l : l[l.index(' ') + 1].isdigit(), logs))
```

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String[] reorderLogFiles(String[] logs) {
        List<String> strs = new ArrayList<>();
        List<String> nums = new ArrayList<>();
        for (String log : logs) {
            if (Character.isLetter(log.charAt(log.indexOf(' ') + 1))) {
                strs.add(log);
            } else {
                nums.add(log);
            }
        }
        strs.sort(new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.substring(o1.indexOf(' ')).compareTo(o2.substring(o2.indexOf(' ')));
            }
        });
        strs.addAll(nums);
        return strs.toArray(new String[0]);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reorder-log-files/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reorder-log-files/description/)

Solution: [LeetCode](https://leetcode.com/articles/reorder-log-files/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reorder-log-files/)