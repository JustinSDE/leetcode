# 49. Group Anagrams | 字母异位词分组

## Question description

<!--If you want to use the English description, use <p>Given an array of strings, group anagrams together.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> <code>[&quot;eat&quot;, &quot;tea&quot;, &quot;tan&quot;, &quot;ate&quot;, &quot;nat&quot;, &quot;bat&quot;]</code>,
<strong>Output:</strong>
[
  [&quot;ate&quot;,&quot;eat&quot;,&quot;tea&quot;],
  [&quot;nat&quot;,&quot;tan&quot;],
  [&quot;bat&quot;]
]</pre>

<p><strong>Note:</strong></p>

<ul>
	<li>All inputs will be in lowercase.</li>
	<li>The order of your output does not&nbsp;matter.</li>
</ul>
 instead-->
<p>给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[&quot;eat&quot;, &quot;tea&quot;, &quot;tan&quot;, &quot;ate&quot;, &quot;nat&quot;, &quot;bat&quot;]</code>,
<strong>输出:</strong>
[
  [&quot;ate&quot;,&quot;eat&quot;,&quot;tea&quot;],
  [&quot;nat&quot;,&quot;tan&quot;],
  [&quot;bat&quot;]
]</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>所有输入均为小写字母。</li>
	<li>不考虑答案输出的顺序。</li>
</ul>


## Note

字母异位词（字母相同，但排列不同的字符串）判断，一般不是做字符统计然后比对统计结果，而是设计一个类似“特征函数”的东西，字母异位词有相同的输出结果。其实这样的特征函数可以很简单：把字符排序一下就行。字母异位词经过字符排序后得到的结果是一样的。


## Solution

Language: **python3**  /  Runtime: 128 ms

```python3
class Solution:
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        d = collections.defaultdict(list)
        for s in strs:
            d[''.join(sorted(s))].append(s)
        return list(d.values())
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/group-anagrams/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/group-anagrams/description/)

Solution: [LeetCode](https://leetcode.com/articles/group-anagrams/)  /  [LeetCode中国](https://leetcode-cn.com/articles/group-anagrams/)