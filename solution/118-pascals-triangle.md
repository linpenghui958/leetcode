```javascript
双重遍历版
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    if (numRows === 0) return [];
    let res = [];
    for(let i = 1; i <= numRows; i++) {
        let tmp = [];
        let preArr = res[i-2] || [];
        for (let j = 0;j < i; j++) {
            if (j === 0) {
                tmp[0] = 1;
            } else {
                let num1 = preArr[j-1] || 0;
                let num2 = preArr[j] || 0;
                tmp[j] = num1 + num2;
            }
        }
      res.push(tmp);
    }
    return res;
};

发现规律，错位相加
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    if (numRows == 0) return [];
    let res = [[1]];
    while(res.length < numRows) {
      let n = res.length;
        let arr1 = [...res[n - 1]];
        let arr2 = [...res[n - 1]];
        arr1.push(0);
        arr2.unshift(0);
        let tmp = [];
        for (let i = 0; i <= res[n - 1].length; i++) {
            tmp[i] = arr1[i] + arr2[i];
        }
        res.push(tmp);
    }
    return res;
};
```