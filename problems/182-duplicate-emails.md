# 182. Duplicate Emails | 查找重复的电子邮箱

## Question description

<!--If you want to use the English description, use <p>Write a SQL query to find all duplicate emails in a table named <code>Person</code>.</p>

<pre>
+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
</pre>

<p>For example, your query should return the following for the above table:</p>

<pre>
+---------+
| Email   |
+---------+
| a@b.com |
+---------+
</pre>

<p><strong>Note</strong>: All emails are in lowercase.</p>
 instead-->
<p>编写一个 SQL 查询，查找&nbsp;<code>Person</code> 表中所有重复的电子邮箱。</p>

<p><strong>示例：</strong></p>

<pre>+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
</pre>

<p>根据以上输入，你的查询应返回以下结果：</p>

<pre>+---------+
| Email   |
+---------+
| a@b.com |
+---------+
</pre>

<p><strong>说明：</strong>所有电子邮箱都是小写字母。</p>


## Note

在用子查询时：

Every derived table must have its own alias

原因：要给子表取个别名。


## Solution

Language: **mysql**  /  Runtime: 401 ms

```mysql
SELECT Email FROM (SELECT Email, COUNT(Email) c FROM Person GROUP BY Email) t WHERE t.c>1;
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/duplicate-emails/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/duplicate-emails/description/)

Solution: [LeetCode](https://leetcode.com/articles/duplicate-emails/)  /  [LeetCode中国](https://leetcode-cn.com/articles/duplicate-emails/)