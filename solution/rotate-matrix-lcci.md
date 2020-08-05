假设数组matrix长度为len
[0, 0] -> [0, len]
[0, 1] -> [1, len]
[0, 2] -> [2, len]
[1, 0] -> [0, len - 1]
通过规律我们可以得出，位置互换的规律
[i, j] - > [len-1-i, j]
最笨的使用额外空间方法
```javascript
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function(matrix) {
  let len = matrix.length;
  // 最简单的傻办法，循环两次，往matrix上赋值
  let res = JSON.parse(JSON.stringify(matrix));
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len; j++) {
      // i j
      matrix[j][len-1-i] = res[i][j];
    }
  }
};
```
不使用额外空间
先按对角线为轴翻转
然后再以水平轴心线为轴翻转
```javascript
let rotate = (matrix) =>{
  for(let i = 0; i < matrix.length; i++){
    for (let j = i; j < matrix[i].length; j++){
      [matrix[i][j],matrix[j][i]] = [matrix[j][i],matrix[i][j]]
    }
  }
  matrix.forEach(row=> row.reverse())
};
```