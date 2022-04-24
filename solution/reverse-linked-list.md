```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
 递归
var reverseList = function(head) {
    if (head.next === null) return head;
    let last = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return last;
};

双指针
var reverseList = function(head) {
    let cur = head;
    let temp = null;
    let pre = null;
    while(cur) {
        temp = cur.next;
        cur.next = pre;
        pre = cur;
        cur = temp;
    }
    return pre;
}
```