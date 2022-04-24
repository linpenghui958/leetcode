```javascript
双指针
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    let res = new ListNode(null, head);
    let fast = res;
    let slow = res;
    // 快指针先走N歩
    while(n > 0) {
        fast = fast.next;
        n--;
    }
    // 同时前进，直到fast到最后，slow则为倒数N前一个节点
    while(fast.next) {
        fast = fast.next;
        slow = slow.next;
    }
    // 删除对应节点
    slow.next = slow.next.next;
    return res.next;
}
```