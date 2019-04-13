# 859. Buddy Strings | 亲密字符串

## Question description

<!--If you want to use the English description, use <p>Given two strings <code>A</code> and <code>B</code>&nbsp;of lowercase letters, return <code>true</code> if and only if we&nbsp;can swap two letters in <code>A</code> so that the result equals <code>B</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">&quot;ab&quot;</span>, B = <span id="example-input-1-2">&quot;ba&quot;</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-2-1">&quot;ab&quot;</span>, B = <span id="example-input-2-2">&quot;ab&quot;</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-3-1">&quot;aa&quot;</span>, B = <span id="example-input-3-2">&quot;aa&quot;</span>
<strong>Output: </strong><span id="example-output-3">true</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-4-1">&quot;aaaaaaabc&quot;</span>, B = <span id="example-input-4-2">&quot;aaaaaaacb&quot;</span>
<strong>Output: </strong><span id="example-output-4">true</span>
</pre>

<div>
<p><strong>Example 5:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-5-1">&quot;&quot;</span>, B = <span id="example-input-5-2">&quot;aa&quot;</span>
<strong>Output: </strong><span id="example-output-5">false</span>
</pre>

<p>&nbsp;</p>

<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt;= 20000</code></li>
	<li><code>0 &lt;= B.length &lt;= 20000</code></li>
	<li><code>A</code> and&nbsp;<code>B</code> consist only of lowercase letters.</li>
</ol>
</div>
</div>
</div>
</div>
</div>
 instead-->
<p>给定两个由小写字母构成的字符串&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;，只要我们可以通过交换 <code>A</code> 中的两个字母得到与 <code>B</code> 相等的结果，就返回&nbsp;<code>true</code>&nbsp;；否则返回 <code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入： </strong>A = &quot;ab&quot;, B = &quot;ba&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入： </strong>A = &quot;ab&quot;, B = &quot;ab&quot;
<strong>输出： </strong>false
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入： </strong>A = &quot;aa&quot;, B = &quot;aa&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入： </strong>A = &quot;aaaaaaabc&quot;, B = &quot;aaaaaaacb&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入： </strong>A = &quot;&quot;, B = &quot;aa&quot;
<strong>输出： </strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt;= 20000</code></li>
	<li><code>0 &lt;= B.length &lt;= 20000</code></li>
	<li><code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;仅由小写字母构成。</li>
</ol>


## Note

这题似乎在答笔试时做过，当时一次性AC，现在却错了好几次，主要是考虑不周全。

如果交换字符串A中两个字符能得到字符串B，则A和B是亲密字符串。

1、如果A和B长度不等，那么必然不是亲密字符串

2、如果A和B长度相等，那么分A和B是否相同两种情况

3、如果A和B相同，要成为亲密字符串，那么只能交换两个相同的字符，因此就进行字符计数，如果有字符出现了两次及以上，那么就是A和B就是亲密字符串，否则就不是。

4、如果A和B长度相同且是不同的字符串，就要用双指针遍历A和B。这里主要需要注意两点：(1)当出现了两处不同且不同之处对称时，不能立即给出判断，还要看后面还有没有不同的；当然，如果有3处不同那么就肯定不是亲密字符串了，如果前面两处不同之处不对称也肯定不是亲密字符串了 (2)由于遇到两处对称不同后不能立即给出判断，因此，在循环结束时要再返回下判断结果，如果前面在3处不同时或前面两处不同不对称时立即返回False，那么这里可以直接返回True，否则就要判断下是否有且仅有两处不同且对称。




## Solution

Language: **python3**  /  Runtime: 32 ms

```python3
class Solution:
    def buddyStrings(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: bool
        """
        if len(A) == len(B):
            if A == B:
                for v in collections.Counter(A).values():
                    if v > 1:
                        return True
                return False
            else:
                tmp = ''
                for i in range(len(A)):
                    x, y = A[i], B[i]
                    if x != y:
                        if tmp:
                            if tmp == y + x:
                                tmp += y + x
                            else:
                                return False
                        else:
                            tmp = x + y
                return True
        else:
            return False
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/buddy-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/buddy-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/buddy-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/buddy-strings/)