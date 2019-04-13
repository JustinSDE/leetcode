# 981. Time Based Key-Value Store | 基于时间的键值存储

## Question description

<!--If you want to use the English description, use <p>Create a timebased key-value store class&nbsp;<code>TimeMap</code>, that supports two operations.</p>

<p>1. <code>set(string key, string value, int timestamp)</code></p>

<ul>
	<li>Stores the <code>key</code> and <code>value</code>, along with the given <code>timestamp</code>.</li>
</ul>

<p>2. <code>get(string key, int timestamp)</code></p>

<ul>
	<li>Returns a value such that <code>set(key, value, timestamp_prev)</code> was called previously, with <code>timestamp_prev &lt;= timestamp</code>.</li>
	<li>If there are multiple such values, it returns the one with the largest <code>timestamp_prev</code>.</li>
	<li>If there are no values, it returns the empty string (<code>&quot;&quot;</code>).</li>
</ul>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>inputs = <span id="example-input-1-1">[&quot;TimeMap&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;]</span>, inputs = <span id="example-input-1-2">[[],[&quot;foo&quot;,&quot;bar&quot;,1],[&quot;foo&quot;,1],[&quot;foo&quot;,3],[&quot;foo&quot;,&quot;bar2&quot;,4],[&quot;foo&quot;,4],[&quot;foo&quot;,5]]</span>
<strong>Output: </strong><span id="example-output-1">[null,null,&quot;bar&quot;,&quot;bar&quot;,null,&quot;bar2&quot;,&quot;bar2&quot;]</span>
<strong>Explanation: </strong><span id="example-output-1">&nbsp; 
TimeMap kv; &nbsp; 
kv.set(&quot;foo&quot;, &quot;bar&quot;, 1); // store the key &quot;foo&quot; and value &quot;bar&quot; along with timestamp = 1 &nbsp; 
kv.get(&quot;foo&quot;, 1);  // output &quot;bar&quot; &nbsp; 
kv.get(&quot;foo&quot;, 3); // output &quot;bar&quot; since there is no value corresponding to foo at timestamp 3 and timestamp 2, then the only value is at timestamp 1 ie &quot;bar&quot; &nbsp; 
kv.set(&quot;foo&quot;, &quot;bar2&quot;, 4); &nbsp; 
kv.get(&quot;foo&quot;, 4); // output &quot;bar2&quot; &nbsp; 
kv.get(&quot;foo&quot;, 5); //output &quot;bar2&quot; &nbsp; 
</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>inputs = <span id="example-input-2-1">[&quot;TimeMap&quot;,&quot;set&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;]</span>, inputs = <span id="example-input-2-2">[[],[&quot;love&quot;,&quot;high&quot;,10],[&quot;love&quot;,&quot;low&quot;,20],[&quot;love&quot;,5],[&quot;love&quot;,10],[&quot;love&quot;,15],[&quot;love&quot;,20],[&quot;love&quot;,25]]</span>
<strong>Output: </strong><span id="example-output-2">[null,null,null,&quot;&quot;,&quot;high&quot;,&quot;high&quot;,&quot;low&quot;,&quot;low&quot;]</span>
</pre>
</div>
</div>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>All key/value strings are lowercase.</li>
	<li>All key/value strings have&nbsp;length in the range&nbsp;<code>[1, 100]</code></li>
	<li>The <code>timestamps</code> for all <code>TimeMap.set</code> operations are strictly increasing.</li>
	<li><code>1 &lt;= timestamp &lt;= 10^7</code></li>
	<li><code>TimeMap.set</code> and <code>TimeMap.get</code>&nbsp;functions will be called a total of <code>120000</code> times (combined) per test case.</li>
</ol>
 instead-->
<p>创建一个基于时间的键值存储类&nbsp;<code>TimeMap</code>，它支持下面两个操作：</p>

<p>1. <code>set(string key, string value, int timestamp)</code></p>

<ul>
	<li>存储键&nbsp;<code>key</code>、值&nbsp;<code>value</code>，以及给定的时间戳&nbsp;<code>timestamp</code>。</li>
</ul>

<p>2. <code>get(string key, int timestamp)</code></p>

<ul>
	<li>返回先前调用&nbsp;<code>set(key, value, timestamp_prev)</code>&nbsp;所存储的值，其中&nbsp;<code>timestamp_prev &lt;= timestamp</code>。</li>
	<li>如果有多个这样的值，则返回对应最大的&nbsp;&nbsp;<code>timestamp_prev</code>&nbsp;的那个值。</li>
	<li>如果没有值，则返回空字符串（<code>&quot;&quot;</code>）。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>inputs = [&quot;TimeMap&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;], inputs = [[],[&quot;foo&quot;,&quot;bar&quot;,1],[&quot;foo&quot;,1],[&quot;foo&quot;,3],[&quot;foo&quot;,&quot;bar2&quot;,4],[&quot;foo&quot;,4],[&quot;foo&quot;,5]]
<strong>输出：</strong>[null,null,&quot;bar&quot;,&quot;bar&quot;,null,&quot;bar2&quot;,&quot;bar2&quot;]
<strong>解释：</strong>&nbsp; 
TimeMap kv; &nbsp; 
kv.set(&quot;foo&quot;, &quot;bar&quot;, 1); // 存储键 &quot;foo&quot; 和值 &quot;bar&quot; 以及时间戳 timestamp = 1 &nbsp; 
kv.get(&quot;foo&quot;, 1);  // 输出 &quot;bar&quot; &nbsp; 
kv.get(&quot;foo&quot;, 3); // 输出 &quot;bar&quot; 因为在时间戳 3 和时间戳 2 处没有对应 &quot;foo&quot; 的值，所以唯一的值位于时间戳 1 处（即 &quot;bar&quot;） &nbsp; 
kv.set(&quot;foo&quot;, &quot;bar2&quot;, 4); &nbsp; 
kv.get(&quot;foo&quot;, 4); // 输出 &quot;bar2&quot; &nbsp; 
kv.get(&quot;foo&quot;, 5); // 输出 &quot;bar2&quot; &nbsp; 

</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>inputs = [&quot;TimeMap&quot;,&quot;set&quot;,&quot;set&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;,&quot;get&quot;], inputs = [[],[&quot;love&quot;,&quot;high&quot;,10],[&quot;love&quot;,&quot;low&quot;,20],[&quot;love&quot;,5],[&quot;love&quot;,10],[&quot;love&quot;,15],[&quot;love&quot;,20],[&quot;love&quot;,25]]
<strong>输出：</strong>[null,null,null,&quot;&quot;,&quot;high&quot;,&quot;high&quot;,&quot;low&quot;,&quot;low&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>所有的键/值字符串都是小写的。</li>
	<li>所有的键/值字符串长度都在&nbsp;<code>[1, 100]</code>&nbsp;范围内。</li>
	<li>所有&nbsp;<code>TimeMap.set</code>&nbsp;操作中的时间戳&nbsp;<code>timestamps</code> 都是严格递增的。</li>
	<li><code>1 &lt;= timestamp &lt;= 10^7</code></li>
	<li><code>TimeMap.set</code> 和&nbsp;<code>TimeMap.get</code>&nbsp;函数在每个测试用例中将（组合）调用总计&nbsp;<code>120000</code> 次。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 195 ms

```java
class Node {
    private int timestamp;
    private String value;

    Node(int timestamp, String value) {
        this.timestamp = timestamp;
        this.value = value;
    }

    public int getTimestamp() {
        return timestamp;
    }

    public void setTimestamp(int timestamp) {
        this.timestamp = timestamp;
    }

    public String getValue() {
        return value;
    }

    public void setValue(String value) {
        this.value = value;
    }
}

class TimeMap {
    private HashMap<String, PriorityQueue<Node>> map;
    public TimeMap() {
        map = new HashMap<>();
    }

    public void set(String key, String value, int timestamp) {
        if (!map.containsKey(key)) {
            map.put(key, new PriorityQueue<>(new Comparator<Node>() {
                @Override
                public int compare(Node o1, Node o2) {
                    return o2.getTimestamp() - o1.getTimestamp();
                }
            }));
        }
        map.get(key).add(new Node(timestamp, value));
    }

    public String get(String key, int timestamp) {
        if (map.containsKey(key)) {
            for (Node o : map.get(key)) {
                if (o.getTimestamp() <= timestamp) {
                    return o.getValue();
                }
            }
        }
        return "";
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/time-based-key-value-store/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/time-based-key-value-store/description/)

Solution: [LeetCode](https://leetcode.com/articles/time-based-key-value-store/)  /  [LeetCode中国](https://leetcode-cn.com/articles/time-based-key-value-store/)