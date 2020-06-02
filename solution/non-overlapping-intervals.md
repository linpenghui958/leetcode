```javascript
/**
 * @param {number[][]} intervals
 * @return {number}
 */
var eraseOverlapIntervals = function(intervals) {
    if (intervals.length === 0) return 0;
    function getNum(arr) {
        let resArr = arr.sort((a,b) => a[1] - b[1]);
        let count = 1;
        let end = resArr[0][1]
        for (let i = 1; i < resArr.length; i++) {
            if (end <= resArr[i][0]) {
                count++
                end = resArr[i][1]
            }
        }
        return count; //求出无重叠的区间数量 
    }
    return intervals.length - getNum(intervals);
};
```