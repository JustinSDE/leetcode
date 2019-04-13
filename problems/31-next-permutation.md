# 31. Next Permutation | 下一个排列

## Question description

<!--If you want to use the English description, use <p>Implement <strong>next permutation</strong>, which rearranges numbers into the lexicographically next greater permutation of numbers.</p>

<p>If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).</p>

<p>The replacement must be <strong><a href="http://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a></strong> and use only constant&nbsp;extra memory.</p>

<p>Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.</p>

<p><code>1,2,3</code> &rarr; <code>1,3,2</code><br />
<code>3,2,1</code> &rarr; <code>1,2,3</code><br />
<code>1,1,5</code> &rarr; <code>1,5,1</code></p>
 instead-->
<p>实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。</p>

<p>如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。</p>

<p>必须<strong><a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95" target="_blank">原地</a></strong>修改，只允许使用额外常数空间。</p>

<p>以下是一些例子，输入位于左侧列，其相应输出位于右侧列。<br>
<code>1,2,3</code> &rarr; <code>1,3,2</code><br>
<code>3,2,1</code> &rarr; <code>1,2,3</code><br>
<code>1,1,5</code> &rarr; <code>1,5,1</code></p>


## Note

从右往左探测，若是不减序列，就反转序列；否则将出现减少处的值与右侧比它大且最接近的值进行交换，并对右侧进行升序排列。


## Solution

Language: **cpp**  /  Runtime: 12 ms

```cpp
class Solution {
public:
    void printVector(vector<int>& nums) {
        cout << "[ ";
        for (int i : nums) {
            cout << i << " ";
        }
        cout << "]" << endl;
    }

    void nextPermutation(vector<int>& nums) {
        if (nums.size() < 2) { return; }
        int p = nums.size() - 2;
        while (p >= 0 && nums[p] >= nums[p+1]) {
            p--;
        }
        if (p == -1) {
            reverse(nums.begin(), nums.end());
        } else {
            for (int i=nums.size()-1; i>p; --i) {
                if (nums[i] > nums[p]) {
                    nums[p] ^= nums[i];
                    nums[i] ^= nums[p];
                    nums[p] ^= nums[i];
                    break;
                }
            }
            sort(nums.begin() + p + 1, nums.end());
        }
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/next-permutation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/next-permutation/description/)

Solution: [LeetCode](https://leetcode.com/articles/next-permutation/)  /  [LeetCode中国](https://leetcode-cn.com/articles/next-permutation/)