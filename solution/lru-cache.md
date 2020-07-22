```javascript
class ListNode {
  constructor(key, val) {
    this.key = key;
    this.val = val;
    this.next = null;
    this.prev = null;
  }
}
/**
 * @param {number} capacity
 */
var LRUCache = function(capacity) {
  this.limitNum = capacity;
  this.cacheNum = 0;
  this.hasMap = {};
  this.dummyHead = new ListNode();
  this.dummyTail = new ListNode();
  this.dummyHead.next = this.dummyTail;
  this.dummyTail.prev = this.dummyHead;
};

/** 
* @param {number} key
* @return {number}
*/
LRUCache.prototype.get = function(key) {
  const node = this.hasMap[key] || null;
  if (node === null) return -1;
  this.moveToHead(node);
  return node.val;
};


/** 
* @param {number} key 
* @param {number} value
* @return {void}
*/
LRUCache.prototype.put = function(key, value) {
  const node = this.hasMap[key] || null;
  if (node === null) {
    let newNode = new ListNode(key, value);
    // 设置值
    this.hasMap[key] = newNode;
    this.cacheNum++;
    // add to head
    this.addToHead(newNode);
    // 判断是否超出数目
    if (this.cacheNum > this.limitNum) {
      // delete last one
      this.remoLastOne();
    }
  } else {
    // 更改值
    node.val = value;
    // add to head
    this.moveToHead(node);
  }
};

LRUCache.prototype.moveToHead = function (node) {
  this.removeNode(node);
  this.addToHead(node);
}

LRUCache.prototype.addToHead = function (node) {
  //add to head
  node.prev = this.dummyHead;
  node.next = this.dummyHead.next;
  this.dummyHead.next.prev = node;
  this.dummyHead.next = node;
}

LRUCache.prototype.removeNode = function (node) {
  //remove
  let tempPrev = node.prev;
  let tempNext = node.next;
  tempPrev.next = tempNext;
  tempNext.prev = tempPrev;
}

LRUCache.prototype.remoLastOne = function() {
  let tailItem = this.dummyTail.prev;
  this.removeNode(tailItem);
  delete this.hasMap[tailItem.key];
  this.cacheNum--;
}

/**
* Your LRUCache object will be instantiated and called as such:
* var obj = new LRUCache(capacity)
* var param_1 = obj.get(key)
* obj.put(key,value)
*/

```