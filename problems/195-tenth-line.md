# 195. Tenth Line | 第十行

## Question description

<!--If you want to use the English description, use <p>Given a text file&nbsp;<code>file.txt</code>, print&nbsp;just the 10th line of the&nbsp;file.</p>

<p><strong>Example:</strong></p>

<p>Assume that <code>file.txt</code> has the following content:</p>

<pre>
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
</pre>

<p>Your script should output the tenth line, which is:</p>

<pre>
Line 10
</pre>

<div class="spoilers"><b>Note:</b><br />
1. If the file contains less than 10 lines, what should you output?<br />
2. There&#39;s at least three different solutions. Try to explore all possibilities.</div>
 instead-->
<p>给定一个文本文件&nbsp;<code>file.txt</code>，请只打印这个文件中的第十行。</p>

<p><strong>示例:</strong></p>

<p>假设&nbsp;<code>file.txt</code> 有如下内容：</p>

<pre>Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
</pre>

<p>你的脚本应当显示第十行：</p>

<pre>Line 10
</pre>

<p><strong>说明:</strong><br>
1. 如果文件少于十行，你应当输出什么？<br>
2. 至少有三种不同的解法，请尝试尽可能多的方法来解题。</p>




## Solution

Language: **bash**  /  Runtime: 4 ms

```bash
# Read from the file file.txt and output the tenth line to stdout.
sed -n '10p' file.txt
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/tenth-line/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/tenth-line/description/)

Solution: [LeetCode](https://leetcode.com/articles/tenth-line/)  /  [LeetCode中国](https://leetcode-cn.com/articles/tenth-line/)