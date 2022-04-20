设计链表

> MyLinkedList linkedList = new MyLinkedList();
linkedList.addAtHead(1);
linkedList.addAtTail(3);
linkedList.addAtIndex(1,2);   //链表变为1-> 2-> 3
linkedList.get(1);            //返回2
linkedList.deleteAtIndex(1);  //现在链表是1-> 3
linkedList.get(1);            //返回3


```javascript
var MyLinkedList = function() {
    this.size = 0;
    this.head = null; // 头结点
    this.tail = null; // 尾节点
};

// 自定义链表
class LinkNode {
    constructor(val, next) {
        this.val = val;
        this.next = next;
    }
}


MyLinkedList.prototype.getNode = function(index) {
    // 边界情况处理
    if(index < 0 || index >= this.size) return null;
    // 虚拟头节点
    let cur = new LinkNode(0, this.head);
    while(index >= 0) {
        cur = cur.next;
        index--;
    }
    return cur;
};

/** 
 * @param {number} index
 * @return {number}
 */
MyLinkedList.prototype.get = function(index) {
    if (index < 0 || index >= this.size) return -1;
    return this.getNode(index).val;
};

/** 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtHead = function(val) {
    let node = new LinkNode(val, this.head);
    this.head = node;
    this.size++;
    if (!this.tail) {
        this.tail = node;
    }
};

/** 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtTail = function(val) {
    let temp = new LinkNode(val, null);
    this.size++;
    if (this.tail) {
        this.tail.next = temp;
        this.tail = temp;
    } else {
        this.tail = temp;
        this.head = temp;
    }
};

/** 
 * @param {number} index 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtIndex = function(index, val) {
    if (index > this.size) return;
    if (index <= 0) {
        this.addAtHead(val)
        return;
    }
    if (index === this.size) {
        this.addAtTail(val)
        return;
    }
    const node = this.getNode(index - 1);
    node.next = new LinkNode(val, node.next);
    this.size++;
};

/** 
 * @param {number} index
 * @return {void}
 */
MyLinkedList.prototype.deleteAtIndex = function(index) {
    if (index < 0 || index >= this.size) return;
    if (index === 0) {
        this.head = this.head.next;
        if (index === this.size - 1) {
            this.tail = this.head;
        }
        this.size--;
        return;
    }
    const node = this.getNode(index - 1);
    node.next = node.next.next;
    if (index === this.size - 1) {
        this.tail = node;
    }
    this.size--;
};
```