# 202. Happy Number | 快乐数

## Question description

<!--If you want to use the English description, use <p>Write an algorithm to determine if a number is &quot;happy&quot;.</p>

<p>A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.</p>

<p><strong>Example:&nbsp;</strong></p>

<pre>
<strong>Input:</strong> 19
<strong>Output:</strong> true
<strong>Explanation: 
</strong>1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre> instead-->
<p>编写一个算法来判断一个数是不是&ldquo;快乐数&rdquo;。</p>

<p>一个&ldquo;快乐数&rdquo;定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是无限循环但始终变不到 1。如果可以变为 1，那么这个数就是快乐数。</p>

<p><strong>示例:&nbsp;</strong></p>

<pre><strong>输入:</strong> 19
<strong>输出:</strong> true
<strong>解释: 
</strong>1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre>




## Solution

Language: **python3**  /  Runtime: 84 ms

```python3
class Solution:
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        num = n
        tmp = {}
        while True:
            num = self.calc(num)
            if num == 1:
                return True
            else:
                if num in tmp:
                    return False
                else:
                    tmp[num] = 0

    def calc(self, n):
        t = list(map(int, list(str(n))))
        res = sum(list(map(lambda x: x ** 2, t)))
        # tt = list(map(lambda x: '%s^2' % str(x), t))
        # print(' + '.join(tt) + ' = ' + str(res))
        return res
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/happy-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/happy-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/happy-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/happy-number/)