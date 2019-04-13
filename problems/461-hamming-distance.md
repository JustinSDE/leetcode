# 461. Hamming Distance | 汉明距离

## Question description

<!--If you want to use the English description, use <p>The <a href="https://en.wikipedia.org/wiki/Hamming_distance" target="_blank">Hamming distance</a> between two integers is the number of positions at which the corresponding bits are different.</p>

<p>Given two integers <code>x</code> and <code>y</code>, calculate the Hamming distance.</p>

<p><b>Note:</b><br />
0 &le; <code>x</code>, <code>y</code> &lt; 2<sup>31</sup>.
</p>

<p><b>Example:</b>
<pre>
<b>Input:</b> x = 1, y = 4

<b>Output:</b> 2

<b>Explanation:</b>
1   (0 0 0 1)
4   (0 1 0 0)
       &uarr;   &uarr;

The above arrows point to positions where the corresponding bits are different.
</pre>
</p> instead-->
<p>两个整数之间的<a href="https://baike.baidu.com/item/%E6%B1%89%E6%98%8E%E8%B7%9D%E7%A6%BB">汉明距离</a>指的是这两个数字对应二进制位不同的位置的数目。</p>

<p>给出两个整数 <code>x</code> 和 <code>y</code>，计算它们之间的汉明距离。</p>

<p><strong>注意：</strong><br />
0 &le; <code>x</code>, <code>y</code> &lt; 2<sup>31</sup>.</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong> x = 1, y = 4

<strong>输出:</strong> 2

<strong>解释:</strong>
1   (0 0 0 1)
4   (0 1 0 0)
       &uarr;   &uarr;

上面的箭头指出了对应二进制位不同的位置。
</pre>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int hammingDistance(int x, int y) {
        int res = 0;
        int z = x ^ y;
        for (int i=0; i<32; ++i) {
            res += 1 & (z >> i);
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/hamming-distance/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/hamming-distance/description/)

Solution: [LeetCode](https://leetcode.com/articles/hamming-distance/)  /  [LeetCode中国](https://leetcode-cn.com/articles/hamming-distance/)