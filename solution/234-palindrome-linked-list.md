##### 递归方法

后续遍历链表
```javascript
var traverse = function (right) {
    if (right === null) return;
    traverse(right.next);
    console.log(right.val)
}
```

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
 * @return {boolean}
 */
let left = null
var isPalindrome = function(head) {
    left = head;
    return traverse(head);
};

var traverse = function (right) {
    if (right === null) return true;

    // 处理val
    console.log(right.val) // 后序遍历节点
    let res = traverse(right.next);
    res = res && (left.val === right.val);
    left = left.next;
    return res;
}
```

##### 双指针方法

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    // 链表长度为0或者为1，均返回true;
    if (head === null) return true;
    if (head && head.next === null) return true;
    let slow = head, fast = head;
    let tmp = head;
    // 通过快满指针找到链表中点
    while(fast !== null && fast.next !== null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    // 奇数情况，fast是链表最后一个位置，slow还需要往前进一步
    if (fast !== null) {
        slow = slow.next; 
    }
    // 反转slow后的链表
    let newNode = traverse(slow);
    while(newNode !== null) {
        console.log(tmp.val, newNode.val)
        if (tmp.val !== newNode.val) {
            return false;
        } else {
            tmp = tmp.next;
            newNode = newNode.next;
        }
    }
    return true;
}

var traverse = function(head) {
    let pre = null, cur = head, nxt = null;
    while(cur !== null) {
        nxt = cur.next;
        cur.next = pre;
        pre = cur;
        cur = nxt;
    }
    return pre;
}

```