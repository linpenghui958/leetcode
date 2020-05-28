```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var minDepth = function(root) {
  if (root === null) return 0;
  const list = [];
  let dep = 1;
  list.push(root);
  
  while(list.length) {
    const size = list.length;
    for (let i = 0; i < size; i++) { // 遍历该层所有的节点
      const node = list.shift();
      if (node.left === null && node.right == null) { // 如果有一个节点满足条件，直接返回
        return dep;
      }
      if (node.left != null) list.push(node.left);
      if (node.right != null) list.push(node.right);
    }
    dep++; // 层级+1
  }
  return dep;
};
```