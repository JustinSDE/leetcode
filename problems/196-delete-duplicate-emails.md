# 196. Delete Duplicate Emails | 删除重复的电子邮箱

## Question description

<!--If you want to use the English description, use <p>Write a SQL query to <strong>delete</strong> all duplicate email entries in a table named <code>Person</code>, keeping only unique emails based on its <i>smallest</i> <b>Id</b>.</p>

<pre>
+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
Id is the primary key column for this table.
</pre>

<p>For example, after running your query, the above <code>Person</code> table should have the following rows:</p>

<pre>
+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+
</pre>

<p><strong>Note:</strong></p>

<p>Your output is the whole <code>Person</code>&nbsp;table after executing your sql. Use <code>delete</code> statement.</p>
 instead-->
<p>编写一个 SQL 查询，来删除&nbsp;<code>Person</code>&nbsp;表中所有重复的电子邮箱，重复的邮箱里只保留&nbsp;<strong>Id&nbsp;</strong><em>最小&nbsp;</em>的那个。</p>

<pre>+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
Id 是这个表的主键。
</pre>

<p>例如，在运行你的查询语句之后，上面的 <code>Person</code> 表应返回以下几行:</p>

<pre>+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+
</pre>




## Solution

Language: **mysql**  /  Runtime: 528 ms

```mysql
# Write your MySQL query statement below
DELETE FROM Person WHERE Id NOT IN (
    SELECT t.Id FROM(
        SELECT MIN(Id) Id FROM Person GROUP BY Email
    ) t
);
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/delete-duplicate-emails/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/delete-duplicate-emails/description/)

Solution: [LeetCode](https://leetcode.com/articles/delete-duplicate-emails/)  /  [LeetCode中国](https://leetcode-cn.com/articles/delete-duplicate-emails/)