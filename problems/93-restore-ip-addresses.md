# 93. Restore IP Addresses | 复原IP地址

## Question description

<!--If you want to use the English description, use <p>Given a string containing only digits, restore it by returning all possible valid IP address combinations.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> &quot;25525511135&quot;
<strong>Output:</strong> <code>[&quot;255.255.11.135&quot;, &quot;255.255.111.35&quot;]
</code></pre>
 instead-->
<p>给定一个只包含数字的字符串，复原它并返回所有可能的 IP 地址格式。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;25525511135&quot;
<strong>输出:</strong> <code>[&quot;255.255.11.135&quot;, &quot;255.255.111.35&quot;]</code></pre>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    void backTracking(string& s, int index, vector<string>& ip, vector<string>& res) {
        int n = 4 - ip.size();
        if (n == 0 && index == (int)s.size()) {
            stringstream ss;
            for (int i=0; i<(int)ip.size(); ++i) {
                if (i > 0) {
                    ss << '.';
                }
                ss << ip[i];
            }
            res.push_back(ss.str());
            return;
        }
        if (s.size() - index > 3 * n || s.size() - index < n) {
            return;
        }
        ip.push_back(s.substr(index, 1));
        backTracking(s, index+1, ip, res);
        ip.pop_back();
        if (s[index] > '0') {
            ip.push_back(s.substr(index, 2));
            backTracking(s, index+2, ip, res);
            ip.pop_back();
        }
        if (s.substr(index, 3) >= "100" && s.substr(index, 3) <= "255") {
            ip.push_back(s.substr(index, 3));
            backTracking(s, index+3, ip, res);
            ip.pop_back();
        }
    }
    
    vector<string> restoreIpAddresses(string s) {
        vector<string> ip;
        vector<string> res;
        backTracking(s, 0, ip, res);
        return res;
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/restore-ip-addresses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/restore-ip-addresses/description/)

Solution: [LeetCode](https://leetcode.com/articles/restore-ip-addresses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/restore-ip-addresses/)