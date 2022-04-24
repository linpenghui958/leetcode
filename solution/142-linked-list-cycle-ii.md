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
var detectCycle = function (head) {
  let slowP = head, fastP = head // 都从头节点出发
  while (fastP) {                // 指向null就说明没有环，返回null
    if (fastP.next == null) return null // fastP.next为null也说明无环
    slowP = slowP.next           // 慢指针走一步
    fastP = fastP.next.next      // 快指针走两步
    if (slowP === fastP) {       // 首次相遇
      fastP = head               // 让快指针回到头节点
      while (true) {             // 开启循环，让快慢指针相遇
        if (slowP === fastP) {   // 相遇地点肯定在入环处
          return slowP
        }
        fastP = fastP.next       // 快慢指针都走一步
        slowP = slowP.next
      }
    }
  }
  return null // head就是null的情况
};
```

![img](../img/linked-list-cycle-2.png);

相遇时  
慢指针走过的步数 `x + y`
快指针走过的步数 `x + y + n(y + z)` ps:y+z为环内一圈

(x + y) * 2 = x + y + n(y + z)
要求x的位置
x + y = n(y + z)
x = (n-1)(y + z) + z ps: n肯定是大于1的

当n=1时，即快指针在圈内刚好走过一圈，合慢指针相遇

即x = z

一个节点从head，一个节点从相遇的位置
同时前进x歩（一起前进即可），即可以走到环的起点