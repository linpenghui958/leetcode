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
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
let successor = null;
var reverseList = function(head, m) {
        if (m === 1) {
            successor = head.next;
            return head;
        }
        let last = reverseList(head.next, m - 1);
        head.next.next = head;
        head.next = successor;
        return last;
    }
var reverseBetween = function(head, m, n) {
    if (m === 1) {
        return reverseList(head, n)
    }
    head.next = reverseBetween(head.next, m - 1, n -1);
    return head;
};
```