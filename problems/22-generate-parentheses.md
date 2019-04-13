# 22. Generate Parentheses | 括号生成

## Question description

<!--If you want to use the English description, use <p>
Given <i>n</i> pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
</p>

<p>
For example, given <i>n</i> = 3, a solution set is:
</p>
<pre>
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
</pre> instead-->
<p>给出&nbsp;<em>n</em>&nbsp;代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且<strong>有效的</strong>括号组合。</p>

<p>例如，给出&nbsp;<em>n </em>=<em> </em>3，生成结果为：</p>

<pre>[
  &quot;((()))&quot;,
  &quot;(()())&quot;,
  &quot;(())()&quot;,
  &quot;()(())&quot;,
  &quot;()()()&quot;
]
</pre>


## Note

很容易想到利用递归来解决。难点主要有：

1、组合不重复

2、组合合法

对于2，可以逐位比较左括号和右括号的个数。对于1，第一次AC时没有想到很好的办法，而是利用`set`的元素不重复性，先把组合存到`set`里再转到`vector`里，这样就实现了组合不重复。


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> res;
        if(!n){
            return res;
        }
        if(n==1){
            res.push_back("()");
            return res;
        }
        vector<string> rst = generateParenthesis(n-1);
        unordered_set<string> tmp;
        for(string rs : rst){
            tmp.insert("()" + rs);
            int ln = 0, rn = 0;
            for(int i=0; i<(int)rs.length(); ++i){
                if(i > 0 && ln >= rn){
                    tmp.insert("(" + rs.substr(0, i) + ")" + rs.substr(i, rs.length()-i));
                }
                ln += (int)(rs.at(i) == '(');
                rn += (int)(rs.at(i) == ')');
            }
            tmp.insert("(" + rs + ")");
        }
        for(string t : tmp){
            res.push_back(t);
        }
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/generate-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/generate-parentheses/description/)

Solution: [LeetCode](https://leetcode.com/articles/generate-parentheses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/generate-parentheses/)