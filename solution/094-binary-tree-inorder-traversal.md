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
 * @return {number[]}
 */
var inorderTraversal = function(root) {
    let result = [];
    let inOrder = function (root) {
        if (!root) return;
        inOrder(root.left);
        result.push(root.val);
        inOrder(root.right);
    }
    inOrder(root);
    return result;
};
```