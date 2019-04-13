# 5018. Camelcase Matching | 驼峰式匹配

## Question description

<!--If you want to use the English description, use <p>A query word matches a given <code>pattern</code> if we can insert <strong>lowercase</strong> letters to the pattern word so that it equals the <code>query</code>. (We may insert each character at any position, and may insert 0 characters.)</p>

<p>Given a list of <code>queries</code>, and a <code>pattern</code>, return an <code>answer</code> list of booleans, where <code>answer[i]</code> is true if and only if <code>queries[i]</code> matches the <code>pattern</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>queries = <span id="example-input-1-1">[&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;]</span>, pattern = <span id="example-input-1-2">&quot;FB&quot;</span>
<strong>Output: </strong><span id="example-output-1">[true,false,true,true,false]</span>
<strong>Explanation: </strong>
&quot;FooBar&quot; can be generated like this &quot;F&quot; + &quot;oo&quot; + &quot;B&quot; + &quot;ar&quot;.
&quot;FootBall&quot; can be generated like this &quot;F&quot; + &quot;oot&quot; + &quot;B&quot; + &quot;all&quot;.
&quot;FrameBuffer&quot; can be generated like this &quot;F&quot; + &quot;rame&quot; + &quot;B&quot; + &quot;uffer&quot;.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>queries = <span id="example-input-2-1">[&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;]</span>, pattern = <span id="example-input-2-2">&quot;FoBa&quot;</span>
<strong>Output: </strong><span id="example-output-2">[true,false,true,false,false]</span>
<strong>Explanation: </strong>
&quot;FooBar&quot; can be generated like this &quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot;.
&quot;FootBall&quot; can be generated like this &quot;Fo&quot; + &quot;ot&quot; + &quot;Ba&quot; + &quot;ll&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>queries = <span id="example-input-3-1">[&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;]</span>, pattern = <span id="example-input-3-2">&quot;FoBaT&quot;</span>
<strong>Output: </strong><span id="example-output-3">[false,true,false,false,false]</span>
<strong>Explanation: </strong>
&quot;FooBarTest&quot; can be generated like this &quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot; + &quot;T&quot; + &quot;est&quot;.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= queries.length &lt;= 100</code></li>
	<li><code>1 &lt;= queries[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= pattern.length &lt;= 100</code></li>
	<li>All strings consists only of lower and upper case English letters.</li>
</ol> instead-->
<p>如果我们可以将<strong>小写字母</strong>插入模式串&nbsp;<code>pattern</code>&nbsp;得到待查询项&nbsp;<code>query</code>，那么待查询项与给定模式串匹配。（我们可以在任何位置插入每个字符，也可以插入 0 个字符。）</p>

<p>给定待查询列表&nbsp;<code>queries</code>，和模式串&nbsp;<code>pattern</code>，返回由布尔值组成的答案列表&nbsp;<code>answer</code>。只有在待查项&nbsp;<code>queries[i]</code> 与模式串&nbsp;<code>pattern</code> 匹配时，&nbsp;<code>answer[i]</code>&nbsp;才为 <code>true</code>，否则为 <code>false</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FB&quot;
<strong>输出：</strong>[true,false,true,true,false]
<strong>示例：</strong>
&quot;FooBar&quot; 可以这样生成：&quot;F&quot; + &quot;oo&quot; + &quot;B&quot; + &quot;ar&quot;。
&quot;FootBall&quot; 可以这样生成：&quot;F&quot; + &quot;oot&quot; + &quot;B&quot; + &quot;all&quot;.
&quot;FrameBuffer&quot; 可以这样生成：&quot;F&quot; + &quot;rame&quot; + &quot;B&quot; + &quot;uffer&quot;.</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FoBa&quot;
<strong>输出：</strong>[true,false,true,false,false]
<strong>解释：</strong>
&quot;FooBar&quot; 可以这样生成：&quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot;.
&quot;FootBall&quot; 可以这样生成：&quot;Fo&quot; + &quot;ot&quot; + &quot;Ba&quot; + &quot;ll&quot;.
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输出：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FoBaT&quot;
<strong>输入：</strong>[false,true,false,false,false]
<strong>解释： </strong>
&quot;FooBarTest&quot; 可以这样生成：&quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot; + &quot;T&quot; + &quot;est&quot;.
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= queries.length &lt;= 100</code></li>
	<li><code>1 &lt;= queries[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= pattern.length &lt;= 100</code></li>
	<li>所有字符串都仅由大写和小写英文字母组成。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    # 缓存递归中间结果
    cache = None

    def sMatch(self, source, p, pattern, q):
        if __class__.cache[p][q] != -1:
            return __class__.cache[p][q]
        tp, tq = p, q
        if q >= len(pattern):
            # 结束匹配，检查是否还有大写字母未匹配
            while p < len(source):
                if source[p].isupper():
                    return False
                p += 1
            __class__.cache[tp][tq] = 1
            return True
        # 若当前要找的是大写字母
        if pattern[q].isupper():
            while p < len(source) and source[p] != pattern[q]:
                # 如果遇到不同的大写字母，则不匹配
                if source[p].isupper():
                    __class__.cache[tp][tq] = 0
                    return False
                p += 1
            # 如果找不到相应的大写字母
            if p == len(source):
                __class__.cache[tp][tq] = 0
                return False
            # 如果有相应的大写字母，继续向右匹配
            return self.sMatch(source, p + 1, pattern, q + 1)
        # 若当前要找的是小写字母
        else:
            # 找对应的小写字母候选位置
            while p < len(source) and source[p].islower():
                if source[p] == pattern[q]:
                    # 针对每个候选位置继续向右匹配
                    if self.sMatch(source, p + 1, pattern, q + 1):
                        __class__.cache[tp][tq] = 1
                        return True
                p += 1
            __class__.cache[tp][tq] = 0
            return False

    def camelMatch(self, queries: List[str], pattern: str) -> List[bool]:
        res = []
        for source in queries:
            __class__.cache = [[-1] * (len(pattern) + 1)] * (len(source) + 1)
            res.append(self.sMatch(source, 0, pattern, 0))
        return res

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/camelcase-matching/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/camelcase-matching/description/)

Solution: [LeetCode](https://leetcode.com/articles/camelcase-matching/)  /  [LeetCode中国](https://leetcode-cn.com/articles/camelcase-matching/)