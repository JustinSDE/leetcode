# 707. Design Linked List | 设计链表

## Question description

<!--If you want to use the English description, use <p>Design your&nbsp;implementation of the linked list. You can choose to use the singly linked list or the doubly linked list. A node in a singly&nbsp;linked list should have two attributes: <code>val</code>&nbsp;and <code>next</code>. <code>val</code> is the value of the current node, and <code>next</code>&nbsp;is&nbsp;a&nbsp;pointer/reference to the next node. If you want to use the doubly linked list,&nbsp;you will need&nbsp;one more attribute <code>prev</code> to indicate the previous node in the linked list. Assume all nodes in the linked list are 0-indexed.</p>

<p>Implement these functions in your linked list class:</p>

<ul>
	<li>get(index) : Get the value of&nbsp;the <code>index</code>-th&nbsp;node in the linked list. If the index is invalid, return <code>-1</code>.</li>
	<li>addAtHead(val) : Add a node of value <code>val</code>&nbsp;before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.</li>
	<li>addAtTail(val) : Append a node of value <code>val</code>&nbsp;to the last element of the linked list.</li>
	<li>addAtIndex(index, val) : Add a node of value <code>val</code>&nbsp;before the <code>index</code>-th&nbsp;node in the linked list.&nbsp;If <code>index</code>&nbsp;equals&nbsp;to the length of&nbsp;linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted.</li>
	<li>deleteAtIndex(index) : Delete&nbsp;the <code>index</code>-th&nbsp;node in the linked list, if the index is valid.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
MyLinkedList linkedList = new MyLinkedList();
linkedList.addAtHead(1);
linkedList.addAtTail(3);
linkedList.addAtIndex(1, 2);  // linked list becomes 1-&gt;2-&gt;3
linkedList.get(1);            // returns 2
linkedList.deleteAtIndex(1);  // now the linked list is 1-&gt;3
linkedList.get(1);&nbsp;&nbsp;&nbsp;         // returns 3
</pre>

<p><strong>Note:</strong></p>

<ul>
	<li>All values will be in the range of <code>[1, 1000]</code>.</li>
	<li>The number of operations will be in the range of&nbsp;<code>[1, 1000]</code>.</li>
	<li>Please do not use the built-in LinkedList library.</li>
</ul>
 instead-->
<p>设计链表的实现。您可以选择使用单链表或双链表。单链表中的节点应该具有两个属性：<code>val</code>&nbsp;和&nbsp;<code>next</code>。<code>val</code>&nbsp;是当前节点的值，<code>next</code>&nbsp;是指向下一个节点的指针/引用。如果要使用双向链表，则还需要一个属性&nbsp;<code>prev</code>&nbsp;以指示链表中的上一个节点。假设链表中的所有节点都是 0-index 的。</p>

<p>在链表类中实现这些功能：</p>

<ul>
	<li>get(index)：获取链表中第&nbsp;<code>index</code>&nbsp;个节点的值。如果索引无效，则返回<code>-1</code>。</li>
	<li>addAtHead(val)：在链表的第一个元素之前添加一个值为&nbsp;<code>val</code>&nbsp;的节点。插入后，新节点将成为链表的第一个节点。</li>
	<li>addAtTail(val)：将值为&nbsp;<code>val</code> 的节点追加到链表的最后一个元素。</li>
	<li>addAtIndex(index,val)：在链表中的第&nbsp;<code>index</code>&nbsp;个节点之前添加值为&nbsp;<code>val</code>&nbsp; 的节点。如果&nbsp;<code>index</code>&nbsp;等于链表的长度，则该节点将附加到链表的末尾。如果 <code>index</code> 大于链表长度，则不会插入节点。</li>
	<li>deleteAtIndex(index)：如果索引&nbsp;<code>index</code> 有效，则删除链表中的第&nbsp;<code>index</code> 个节点。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre>MyLinkedList linkedList = new MyLinkedList();
linkedList.addAtHead(1);
linkedList.addAtTail(3);
linkedList.addAtIndex(1,2);   //链表变为1-&gt; 2-&gt; 3
linkedList.get(1);            //返回2
linkedList.deleteAtIndex(1);  //现在链表是1-&gt; 3
linkedList.get(1);            //返回3
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>所有值都在&nbsp;<code>[1, 1000]</code>&nbsp;之内。</li>
	<li>操作次数将在&nbsp;&nbsp;<code>[1, 1000]</code>&nbsp;之内。</li>
	<li>请不要使用内置的 LinkedList 库。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 55 ms

```java
class MyLinkedList {
    
    class Node {
        int val;
        Node next;
        
        Node (int val) {
            this.val = val;
            this.next = null;
        }
    }

    Node head;

    /** Initialize your data structure here. */
    public MyLinkedList() {
        head = new Node(-1);
    }
    
    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    public int get(int index) {
        Node t = head;
        for (int i = 0; i <= index; i++) {
            if (t == null) return -1;
            t = t.next;
        }
        return t == null ? -1 : t.val;
    }
    
    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    public void addAtHead(int val) {
        Node t = new Node(val);
        t.next = head.next;
        head.next = t;
    }
    
    /** Append a node of value val to the last element of the linked list. */
    public void addAtTail(int val) {
        Node t = head;
        while (t.next != null) {
            t = t.next;
        }
        t.next = new Node(val);
    }
    
    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    public void addAtIndex(int index, int val) {
        if (index < 0) {
            addAtHead(val);
        }
        Node t = head;
        for (int i = 0; i < index; i++) {
            if (t == null) return;
            t = t.next;
        }
        if (t != null) {
            Node p = t.next;
            t.next = new Node(val);
            if (p != null) {
                t.next.next = p;
            }
        }
    }
    
    /** Delete the index-th node in the linked list, if the index is valid. */
    public void deleteAtIndex(int index) {
        if (index < 0) return;
        Node t = head;
        for (int i = 0; i < index; i++) {
            if (t == null) return;
            t = t.next;
        }
        if (t == null) return;
        Node p = t.next;
        if (p != null) {
            t.next = p.next;
            p.next = null;
        }
    }
}

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/design-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/design-linked-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/design-linked-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/design-linked-list/)