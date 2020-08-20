```javascript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
    if (rowIndex == 0) return [1];
    if (rowIndex == 1) return [1, 1];
    let res = [1, 1];
    let index = 1
    for (let i = 2; i < rowIndex + 1; i++) {
        let tmp = [];
        let arr1 = [...res];
        let arr2 = [...res];
        arr1.push(0);
        arr2.unshift(0);
        for (let j = 0; j <= res.length; j++) {
            tmp[j] = arr1[j] + arr2[j];
        }
        res = tmp
    }
    return res;
};
```