# 284. Peeking Iterator | 顶端迭代器

## Question description

<!--If you want to use the English description, use <p>Given an Iterator class interface with methods: <code>next()</code> and <code>hasNext()</code>, design and implement a PeekingIterator that support the <code>peek()</code> operation -- it essentially peek() at the element that will be returned by the next call to next().</p>

<p><strong>Example:</strong></p>

<pre>
Assume that the iterator is initialized to the beginning of the list: <strong><code>[1,2,3]</code></strong>.

Call <strong><code>next()</code></strong> gets you <strong>1</strong>, the first element in the list.
Now you call <strong><code>peek()</code></strong> and it returns <strong>2</strong>, the next element. Calling <strong><code>next()</code></strong> after that <i><b>still</b></i> return <strong>2</strong>. 
You call <strong><code>next()</code></strong> the final time and it returns <strong>3</strong>, the last element. 
Calling <strong><code>hasNext()</code></strong> after that should return <strong>false</strong>.
</pre>

<p><b>Follow up</b>: How would you extend your design to be generic and work with all types, not just integer?</p>
 instead-->
<p>给定一个迭代器类的接口，接口包含两个方法：&nbsp;<code>next()</code>&nbsp;和&nbsp;<code>hasNext()</code>。设计并实现一个支持&nbsp;<code>peek()</code>&nbsp;操作的顶端迭代器 -- 其本质就是把原本应由&nbsp;<code>next()</code>&nbsp;方法返回的元素&nbsp;<code>peek()</code>&nbsp;出来。</p>

<p><strong>示例:</strong></p>

<pre>假设迭代器被初始化为列表&nbsp;<strong><code>[1,2,3]</code></strong>。

调用&nbsp;<strong><code>next() </code></strong>返回 <strong>1</strong>，得到列表中的第一个元素。
现在调用&nbsp;<strong><code>peek()</code></strong>&nbsp;返回 <strong>2</strong>，下一个元素。在此之后调用&nbsp;<strong><code>next() </code></strong>仍然返回 <strong>2</strong>。
最后一次调用&nbsp;<strong><code>next()</code></strong>&nbsp;返回 <strong>3</strong>，末尾元素。在此之后调用&nbsp;<strong><code>hasNext()</code></strong>&nbsp;应该返回 <strong>false</strong>。
</pre>

<p><strong>进阶：</strong>你将如何拓展你的设计？使之变得通用化，从而适应所有的类型，而不只是整数型？</p>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
// Below is the interface for Iterator, which is already defined for you.
// **DO NOT** modify the interface for Iterator.
class Iterator {
    struct Data;
    Data* data;
public:
    Iterator(const vector<int>& nums);
    Iterator(const Iterator& iter);
    virtual ~Iterator();
    // Returns the next element in the iteration.
    int next();
    // Returns true if the iteration has more elements.
    bool hasNext() const;
};


class PeekingIterator : public Iterator {
public:
    int pos = 0;
    vector<int> vec;
    PeekingIterator(const vector<int>& nums) : Iterator(nums) {
        // Initialize any member here.
        // **DO NOT** save a copy of nums and manipulate it directly.
        // You should only use the Iterator interface methods.
        vec = nums;
    }

    // Returns the next element in the iteration without advancing the iterator.
    int peek() {
        return vec[pos];
    }

    // hasNext() and next() should behave the same as in the Iterator interface.
    // Override them if needed.
    int next() {
        int t = peek();
        pos++;
        return t;
    }

    bool hasNext() const {
        return pos < vec.size();
    }
};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/peeking-iterator/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/peeking-iterator/description/)

Solution: [LeetCode](https://leetcode.com/articles/peeking-iterator/)  /  [LeetCode中国](https://leetcode-cn.com/articles/peeking-iterator/)