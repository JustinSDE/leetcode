# 551. Student Attendance Record I | 学生出勤记录 I

## Question description

<!--If you want to use the English description, use You are given a string representing an attendance record for a student. The record only contains the following three characters:

<p>
<ol>
<li><b>'A'</b> : Absent. </li>
<li><b>'L'</b> : Late.</li>
<li> <b>'P'</b> : Present. </li>
</ol>
</p>

<p>
A student could be rewarded if his attendance record doesn't contain <b>more than one 'A' (absent)</b> or <b>more than two continuous 'L' (late)</b>.    </p>

<p>You need to return whether the student could be rewarded according to his attendance record.</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> "PPALLP"
<b>Output:</b> True
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> "PPALLL"
<b>Output:</b> False
</pre>
</p>


 instead-->
<p>给定一个字符串来代表一个学生的出勤记录，这个记录仅包含以下三个字符：</p>

<ol>
	<li><strong>&#39;A&#39;</strong> : Absent，缺勤</li>
	<li><strong>&#39;L&#39;</strong> : Late，迟到</li>
	<li><strong>&#39;P&#39;</strong> : Present，到场</li>
</ol>

<p>如果一个学生的出勤记录中不<strong>超过一个&#39;A&#39;(缺勤)</strong>并且<strong>不超过两个连续的&#39;L&#39;(迟到)</strong>,那么这个学生会被奖赏。</p>

<p>你需要根据这个学生的出勤记录判断他是否会被奖赏。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;PPALLP&quot;
<strong>输出:</strong> True
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot;PPALLL&quot;
<strong>输出:</strong> False
</pre>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def checkRecord(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if s.count('A') > 1 or 'LLL' in s:
            return False
        return True
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/student-attendance-record-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/student-attendance-record-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/student-attendance-record-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/student-attendance-record-i/)