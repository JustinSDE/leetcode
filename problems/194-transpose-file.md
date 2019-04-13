# 194. Transpose File | 转置文件

## Question description

<!--If you want to use the English description, use <p>Given a text file <code>file.txt</code>, transpose its content.</p>

<p>You may assume that each row has the same number of columns and each field is separated by the <code>&#39; &#39;</code> character.</p>

<p><strong>Example:</strong></p>

<p>If <code>file.txt</code> has the following content:</p>

<pre>
name age
alice 21
ryan 30
</pre>

<p>Output the following:</p>

<pre>
name alice ryan
age 21 30
</pre>

<p>&nbsp;</p>
 instead-->
<p>给定一个文件&nbsp;<code>file.txt</code>，转置它的内容。</p>

<p>你可以假设每行列数相同，并且每个字段由&nbsp;<code>&#39; &#39;</code> 分隔.</p>

<p><strong>示例:</strong></p>

<p>假设&nbsp;<code>file.txt</code>&nbsp;文件内容如下：</p>

<pre>name age
alice 21
ryan 30
</pre>

<p>应当输出：</p>

<pre>name alice ryan
age 21 30
</pre>




## Solution

Language: **bash**  /  Runtime: 16 ms

```bash
# Read from the file file.txt and print its transposed content to stdout.

# using awk for this purpose
awk '
    {
        for(i=1; i<=NF; i++)
        {   
            if(line[i] == "")
            {
                line[i] = $i
            }
            else
            {
                line[i] = line[i]" "$i
            }
        }
    }
    END{
         for(i=1; i<=NF; i++)
         {
             print line[i]
         }
       }
    ' file.txt
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/transpose-file/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/transpose-file/description/)

Solution: [LeetCode](https://leetcode.com/articles/transpose-file/)  /  [LeetCode中国](https://leetcode-cn.com/articles/transpose-file/)