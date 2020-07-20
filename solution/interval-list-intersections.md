```javascript
/**
 * @param {number[][]} A
 * @param {number[][]} B
 * @return {number[][]}
 */
var intervalIntersection = function(A, B) {
    let i = 0, j = 0;
    let res = [];
    while(i < A.length && j < B.length) {
        let [a1, a2] = A[i];
        let [b1, b2] = B[j];
        if (!(a2 < b1 || a1 > b2)) { // 两个区间没有交集的情况取反，即为有交集的情况
            res.push([Math.max(a1,b1), Math.min(a2,b2)]); // 获取相交区间的起始
        }
        if (a2 < b2) { // 如果结束位置b2更大，则前进A数组的下标继续跟b2比较
            i++;
        } else {
            j++;
        }
    }
    return res;
};
```