```javascript
/**
 * @param {number[]} weights
 * @param {number} D
 * @return {number}
 */
var shipWithinDays = function(weights, D) {
    // 最大，最小可能的值
    let min = Math.min(...weights);
    let max = weights.reduce((sum, cur) => sum + cur, 0);
    let left = min;
    let right = max + 1;
    // 二分查找，左边界，最小情况
    while(left < right) { 
        let mid = Math.floor(left + ( right - left ) / 2);
        if (canFinish(weights, D, mid)) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
};

var canFinish = function(w, D, cap) {
    let i = 0;
    for (let day = 0; day < D; day++) {
        let maxCap = cap;
        while((maxCap -= w[i]) >= 0) {
            i++;
            if (i === w.length) {
                return true;
            }
        }
    }
    return false;
}
```