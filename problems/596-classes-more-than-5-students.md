# 596. Classes More Than 5 Students | 超过5名学生的课

## Question description

<!--If you want to use the English description, use <p>There is a table <code>courses</code> with columns: <b>student</b> and <b>class</b></p>

<p>Please list out all classes which have more than or equal to 5 students.</p>

<p>For example, the table:</p>

<pre>
+---------+------------+
| student | class      |
+---------+------------+
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |
+---------+------------+
</pre>

<p>Should output:</p>

<pre>
+---------+
| class   |
+---------+
| Math    |
+---------+
</pre>

<p>&nbsp;</p>

<p><b>Note:</b><br />
The students should not be counted duplicate in each course.</p>
 instead-->
<p>有一个<code>courses</code> 表 ，有: <strong>student&nbsp;(学生) </strong>和 <strong>class (课程)</strong>。</p>

<p>请列出所有超过或等于5名学生的课。</p>

<p>例如,表:</p>

<pre>
+---------+------------+
| student | class      |
+---------+------------+
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |
+---------+------------+
</pre>

<p>应该输出:</p>

<pre>
+---------+
| class   |
+---------+
| Math    |
+---------+
</pre>

<p><strong>Note:</strong><br />
学生在每个课中不应被重复计算。</p>




## Solution

Language: **mysql**  /  Runtime: 1548 ms

```mysql
# Write your MySQL query statement below
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) > 4;
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/classes-more-than-5-students/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/classes-more-than-5-students/description/)

Solution: [LeetCode](https://leetcode.com/articles/classes-more-than-5-students/)  /  [LeetCode中国](https://leetcode-cn.com/articles/classes-more-than-5-students/)