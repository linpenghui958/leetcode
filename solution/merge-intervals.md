```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function(intervals) {
    if (intervals.length === 0) return [];

    intervals.sort((a,b) => a[0] - b[0]); // [start, ned]按照start升序排列
    let res = [];

    res.push(intervals[0]); // start最小的开始判断

    for (let i = 0; i < intervals.length; i++) {
        const curr = intervals[i];
        const last = res.length - 1;
        if (res[last] && curr[0] <= res[last][1]) { // 跟当前res中最新区间的end进行比较，如果当前start小于区间的end，则表示两个区间有交集
            res[last][1] = Math.max(curr[1], res[last][1])
        } else { // 否则为没有交集，将当前最新的区间放到res最后
            res[last+1] = curr;
        }
    }
    return res;
};
```