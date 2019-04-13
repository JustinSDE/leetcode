# 595. Big Countries | 大的国家

## Question description

<!--If you want to use the English description, use <p>There is a table <code>World</code></p>

<pre>
+-----------------+------------+------------+--------------+---------------+
| name            | continent  | area       | population   | gdp           |
+-----------------+------------+------------+--------------+---------------+
| Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
| Albania         | Europe     | 28748      | 2831741      | 12960000      |
| Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
| Andorra         | Europe     | 468        | 78115        | 3712000       |
| Angola          | Africa     | 1246700    | 20609294     | 100990000     |
+-----------------+------------+------------+--------------+---------------+
</pre>

<p>A country is big if it has an area of bigger than 3 million square km or a population of more than 25 million.</p>

<p>Write a SQL solution to output big countries&#39; name, population and area.</p>

<p>For example, according to the above table, we should output:</p>

<pre>
+--------------+-------------+--------------+
| name         | population  | area         |
+--------------+-------------+--------------+
| Afghanistan  | 25500100    | 652230       |
| Algeria      | 37100000    | 2381741      |
+--------------+-------------+--------------+
</pre>

<p>&nbsp;</p>
 instead-->
<p>这里有张&nbsp;<code>World</code> 表</p>

<pre>+-----------------+------------+------------+--------------+---------------+
| name            | continent  | area       | population   | gdp           |
+-----------------+------------+------------+--------------+---------------+
| Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
| Albania         | Europe     | 28748      | 2831741      | 12960000      |
| Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
| Andorra         | Europe     | 468        | 78115        | 3712000       |
| Angola          | Africa     | 1246700    | 20609294     | 100990000     |
+-----------------+------------+------------+--------------+---------------+
</pre>

<p>如果一个国家的面积超过300万平方公里，或者人口超过2500万，那么这个国家就是大国家。</p>

<p>编写一个SQL查询，输出表中所有大国家的名称、人口和面积。</p>

<p>例如，根据上表，我们应该输出:</p>

<pre>+--------------+-------------+--------------+
| name         | population  | area         |
+--------------+-------------+--------------+
| Afghanistan  | 25500100    | 652230       |
| Algeria      | 37100000    | 2381741      |
+--------------+-------------+--------------+
</pre>




## Solution

Language: **mysql**  /  Runtime: 2024 ms

```mysql
SELECT name, population, area FROM World WHERE area>3000000 OR population>25000000;
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/big-countries/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/big-countries/description/)

Solution: [LeetCode](https://leetcode.com/articles/big-countries/)  /  [LeetCode中国](https://leetcode-cn.com/articles/big-countries/)