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
 * @param {number} k
 * @return {ListNode}
 */
// 翻转链表的a到b
var reverse = function (a, b) {
  let pre = null, cur = a, nxt = a;
  while(cur !== b) {
    nxt = cur.next;
    cur.next = pre;
    pre = cur;
    cur = nxt;
  }
  return pre;
}   

var reverseKGroup = function(head, k) {
    if (head === null) return null;

    let a = head; // 反转起始位置
    let b = head; // 反转结束位置
    // 检查能否到达结束位置，如果剩余的长度不够，直接返回
    for (let i = 0; i < k; i++) {
      if (b === null) return head;
      b = b.next;
    }
    // 翻转第一段
    let newHead = reverse(a, b);
    // 递归剩下的，**反转后a为链表结尾**
    a.next = reverseKGroup(b, k);
    // 返回新的头结点
    return newHead;
};
```

- 翻转链表

```javascript
var reverse = function (a) {
  let pre = null, cur = a, nxt = null;
  while(cur !== null) {
    nxt = cur.next;
    cur.next = pre;
    pre = cur;
    cur = nxt;
  }
  return pre;
}   
```

- 翻转链表 从a节点到b节点

```javascript
var reverse = function (a, b) {
  let pre = null, cur = a, nxt = bull;
  while(cur !== b) {
    nxt = cur.next;
    cur.next = pre;
    pre = cur;
    cur = nxt;
  }
  return pre;
}   
```