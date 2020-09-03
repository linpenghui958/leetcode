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
// 层序遍历
var maxDepth = function(root) {
  if (!root.val) return 0;
  let stack = [];
  let dep = 0;
  stack.push(root);
  while(stack.length) {
    let tmp = [];
    for (let node of stack) {
      if (node.left) tmp.push(node.left);
      if (node.right) tmp.push(node.right);
    } 
    stack = tmp;
    dep++;
  }
  return dep;
};

// 递归处理
var maxDepth = function(root) {
  if (!root) return 0;
  return Math.max(maxDepth(root.left) + 1, maxDepth(root.right) + 1);
};
```