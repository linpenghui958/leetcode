删除某个节点
cur.next = cur.next.next

当第一个节点需要剔除的时候
1. 特殊处理
2. 设置一个虚拟头结点

```javascript
/**
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
	// 虚拟头节点，最终返回res.next
	let res = new ListNode(0, head);
	let cur = res;
	while(cur.next) {
		if (cur.next.val === val) {
			// 删除当前节点
			cur.next = cur.next.next;
			// 删除情况不需要前进一格
			continue;
		}
		// 前进一格
		cur = cur.next;
	} 
	return res.next;
}

```