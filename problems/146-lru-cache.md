# 146. LRU Cache | LRU缓存机制

## Question description

<!--If you want to use the English description, use <p>
Design and implement a data structure for <a href="https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU" target="_blank">Least Recently Used (LRU) cache</a>. It should support the following operations: <code>get</code> and <code>put</code>.
</p>

<p>
<code>get(key)</code> - Get the value (will always be positive) of the key if the key exists in the cache, otherwise return -1.<br>
<code>put(key, value)</code> - Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.
</p>

<p><b>Follow up:</b><br />
Could you do both operations in <b>O(1)</b> time complexity?</p>

<p><b>Example:</b>
<pre>
LRUCache cache = new LRUCache( 2 /* capacity */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // returns 1
cache.put(3, 3);    // evicts key 2
cache.get(2);       // returns -1 (not found)
cache.put(4, 4);    // evicts key 1
cache.get(1);       // returns -1 (not found)
cache.get(3);       // returns 3
cache.get(4);       // returns 4
</pre>
</p> instead-->
<p>运用你所掌握的数据结构，设计和实现一个&nbsp; <a href="https://baike.baidu.com/item/LRU" target="_blank">LRU (最近最少使用) 缓存机制</a>。它应该支持以下操作： 获取数据 <code>get</code> 和 写入数据 <code>put</code> 。</p>

<p>获取数据 <code>get(key)</code> - 如果密钥 (key) 存在于缓存中，则获取密钥的值（总是正数），否则返回 -1。<br>
写入数据 <code>put(key, value)</code> - 如果密钥不存在，则写入其数据值。当缓存容量达到上限时，它应该在写入新数据之前删除最近最少使用的数据值，从而为新的数据值留出空间。</p>

<p><strong>进阶:</strong></p>

<p>你是否可以在&nbsp;<strong>O(1)</strong> 时间复杂度内完成这两种操作？</p>

<p><strong>示例:</strong></p>

<pre>LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得密钥 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得密钥 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4
</pre>


## Note

<!--#221425311-->


## Solution

Language: **java**  /  Runtime: 63 ms

```java
class LRUCache {
    class Cache extends LinkedHashMap {
        private int capacity;

        public Cache(int capacity) {
            super(capacity, 0.75f, true);
            this.capacity = capacity;
        }

        @Override
        protected boolean removeEldestEntry(Map.Entry eldest) {
            return size() > this.capacity;
        }
    }

    private Cache cache;

    public LRUCache(int capacity) {
        cache = new Cache(capacity);
    }

    public int get(int key) {
        return (int)cache.getOrDefault(key, -1);
    }

    public void put(int key, int value) {
        cache.put(key, value);
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/lru-cache/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lru-cache/description/)

Solution: [LeetCode](https://leetcode.com/articles/lru-cache/)  /  [LeetCode中国](https://leetcode-cn.com/articles/lru-cache/)