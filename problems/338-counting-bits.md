# 338. Counting Bits | 比特位计数

## Question description

<!--If you want to use the English description, use <p>Given a non negative integer number <b>num</b>. For every numbers <b>i</b> in the range <b>0 &le; i &le; num</b> calculate the number of 1&#39;s in their binary representation and return them as an array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">2</span>
<strong>Output: </strong><span id="example-output-1">[0,1,1]</span></pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">5</span>
<strong>Output: </strong><code>[0,1,1,2,1,2]</code>
</pre>

<p><b>Follow up:</b></p>

<ul>
	<li>It is very easy to come up with a solution with run time <b>O(n*sizeof(integer))</b>. But can you do it in linear time <b>O(n)</b> /possibly in a single pass?</li>
	<li>Space complexity should be <b>O(n)</b>.</li>
	<li>Can you do it like a boss? Do it without using any builtin function like <b>__builtin_popcount</b> in c++ or in any other language.</li>
</ul> instead-->
<p>给定一个非负整数&nbsp;<strong>num</strong>。对于&nbsp;<strong>0 &le; i &le; num </strong>范围中的每个数字&nbsp;<strong>i&nbsp;</strong>，计算其二进制数中的 1 的数目并将它们作为数组返回。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>[0,1,1]</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>5
<strong>输出: </strong><code>[0,1,1,2,1,2]</code></pre>

<p><strong>进阶:</strong></p>

<ul>
	<li>给出时间复杂度为<strong>O(n*sizeof(integer))</strong>的解答非常容易。但你可以在线性时间<strong>O(n)</strong>内用一趟扫描做到吗？</li>
	<li>要求算法的空间复杂度为<strong>O(n)</strong>。</li>
	<li>你能进一步完善解法吗？要求在C++或任何其他语言中不使用任何内置函数（如 C++ 中的&nbsp;<strong>__builtin_popcount</strong>）来执行此操作。</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 116 ms

```python3
class Solution:
    def countBits(self, num):
        """
        :type num: int
        :rtype: List[int]
        """
        tmp = [0]
        for i in range(1, num+1):
            tmp.append(tmp[i>>1] + i%2)
        return tmp
```

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int[] countBits(int num) {
        int[] f = new int[num + 1];
        for (int i=1; i<=num; i++) f[i] = f[i >> 1] + (i & 1);
    return f;
}
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/counting-bits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/counting-bits/description/)

Solution: [LeetCode](https://leetcode.com/articles/counting-bits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/counting-bits/)