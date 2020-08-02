```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node.
 * @param {ListNode} head
 */
var Solution = function(head) {
    this.head = head;
};

/**
 * Returns a random node's value.
 * @return {number}
 */
Solution.prototype.getRandom = function() {
    let res = 0;
    let i = 0;
    let p = this.head;
    while( p !== null ) {
        // 每一次返回 [0, i)中的随机数，那么随机数random等于0的概率为 1/n
        const random = Math.floor((Math.random() * (++i)));
        if (random === 0) {
            res = p.val;
        }
        p = p.next;
    }
    return res;
};
```