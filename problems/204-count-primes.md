# 204. Count Primes | 计数质数

## Question description

<!--If you want to use the English description, use <p>Count the number of prime numbers less than a non-negative number, <b><i>n</i></b>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
</pre>
 instead-->
<p>统计所有小于非负整数&nbsp;<em>n&nbsp;</em>的质数的数量。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 10
<strong>输出:</strong> 4
<strong>解释:</strong> 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
</pre>




## Solution

Language: **python3**  /  Runtime: 216 ms

```python3
class Solution:
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n < 2: return 0
        if n == 2: return 0
        res = 1
        
        trueTable = [True]*n
        trueTable[0:2] = [False]*2
        for i in range(2, int(n**0.5) + 1):
            if trueTable[i] == True:
                trueTable[i*2:n:i] = [False]*((n - 1 - i*2)//i + 1)
        return sum(trueTable)
        # return sum([self.isPrime(x) for x in range(n)])

    def isPrime(self, n):
        if n < 2:
            return False
        if n in (2, 3):
            return True
        if n % 6 not in (1, 5):
            return False
        for i in range(2, int(n**0.5)+1):
            if n % i == 0:
                return False
        return True
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-primes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-primes/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-primes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-primes/)