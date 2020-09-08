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
var preorderTraversal = function(root) {
    let result = []
    var preOrderTraverseNode = (node) => {
        if(node) {
            // 先根节点
            result.push(node.val)
            // 然后遍历左子树
            preOrderTraverseNode(node.left)
            // 再遍历右子树
            preOrderTraverseNode(node.right)
        }
    }
    preOrderTraverseNode(root)
    return result
};
```