# 1. Two Sum | 两数之和

## Question description

<!--If you want to use the English description, use <p>Given an array of integers, return <strong>indices</strong> of the two numbers such that they add up to a specific target.</p>

<p>You may assume that each input would have <strong><em>exactly</em></strong> one solution, and you may not use the <em>same</em> element twice.</p>

<p><strong>Example:</strong></p>

<pre>
Given nums = [2, 7, 11, 15], target = 9,

Because nums[<strong>0</strong>] + nums[<strong>1</strong>] = 2 + 7 = 9,
return [<strong>0</strong>, <strong>1</strong>].
</pre>

<p>&nbsp;</p>
 instead-->
<p>给定一个整数数组 <code>nums</code>&nbsp;和一个目标值 <code>target</code>，请你在该数组中找出和为目标值的那&nbsp;<strong>两个</strong>&nbsp;整数，并返回他们的数组下标。</p>

<p>你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。</p>

<p><strong>示例:</strong></p>

<pre>给定 nums = [2, 7, 11, 15], target = 9

因为 nums[<strong>0</strong>] + nums[<strong>1</strong>] = 2 + 7 = 9
所以返回 [<strong>0, 1</strong>]
</pre>


## Note

这是LeetCode的第一题。再次看到本题，发现上次提交已是两年前，感触良多。查看上次提交的代码，居然采用暴力枚举的方式。这些年确实成长了许多，还要不断学习。

虽然这题比较简单，但还是有一些地方需要注意：

1、数字为目标的一半，此时该数字应该在数组中出现两次

2、因为要返回索引数组，所以，要记录索引

3、没必要遍历，因为如果找到了就可以立即返回

因此，比较好的做法是，用HashMap记录数字的索引，每次都看差值是否在该HashMap中，如果在就可以返回结果，否则，就记录索引。


## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
                int j = map.get(target - nums[i]);
                return new int[]{j, i};
            } else {
                map.put(nums[i], i);
            }
        }
        return new int[]{};
    }
}

```

Language: **python**  /  Runtime: 24 ms

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        info = dict()
        for i, num in enumerate(nums):
            if target - num in info:
                return [info[target - num], i]
            else:
                info[num] = i
```

Language: **cpp**  /  Runtime: 8 ms

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> info;
        for(int i=0; i<nums.size(); i++){
            if(info.count(target - nums[i])){
                return vector<int>{info.at(target - nums[i]), i};
            }else{
                info[nums[i]] = i;
            }
        }
    }
};
```

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        info = dict()
        for i, num in enumerate(nums):
            if target - num in info:
                return [info[target - num], i]
            else:
                info[num] = i

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/two-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/two-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/two-sum/)