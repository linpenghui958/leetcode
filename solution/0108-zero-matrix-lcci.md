```javascript
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var setZeroes = function(matrix) {
  // 先找到为0的，然后保存一个横向，竖向需要清零的set
  const row = new Set();
  const column = new Set();
  const len = matrix.length;
  for (let i = 0; i < len; i++) {
    let jlen = matrix[i].length;
    for (let j = 0; j < jlen; j++) {
      if (matrix[i][j] === 0) {
        row.add(i);
        column.add(j);
      }
    }
  }
  // 清空该位置
  for (let i = 0; i < len; i++) {
    let jlen = matrix[i].length;
    for (let j = 0; j < jlen; j++) {
      if (row.has(i) || column.has(j)) {
        matrix[i][j] = 0;
      }
    }
  }
};
```