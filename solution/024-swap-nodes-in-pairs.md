

```javascript
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var swapPairs = function(head) {
    let res = new ListNode(null, head);
    let cur = res;
    // 存在后续两个节点需要交换的情况
    while(cur.next && cur.next.next) {
        let temp = cur.next;
        let temp1 = cur.next.next.next;

        cur.next = cur.next.next;
        cur.next.next = temp;
        cur.next.next.next = temp1;

        cur = cur.next.next;
    }
    return res.next;
}
```