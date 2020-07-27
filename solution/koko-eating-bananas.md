```javascript
/**
 * @param {number[]} piles
 * @param {number} H
 * @return {number}
 */

var minEatingSpeed = function(piles, H) {
    // 暴力解法
    const Max = Math.max(...piles);
    // 从1循环到Max看最小情况
    for (let speed = 1; speed < Max; speed++) {
        if (canFinish(piles, speed, H)) {
            return speed
        }
    }
    return Max;
};

var minEatingSpeed = function(piles, H) {
    const Max = Math.max(...piles);
    let left = 1;
    let right = Max + 1;
    // 二分查找，寻找左边界
    while(left < right) {
        let mid = Math.floor(left + ( right - left ) / 2);
        if (canFinish(piles, mid, H)) {
            right = mid
        } else {
            left = mid + 1;
        }
    }
    return left;
};

var canFinish = function(piles, speed, H) {
    let time = 0;
    for (let num of piles) {
        time = time + Math.ceil(num / speed);
    }
    return time <= H;
}

console.log(minEatingSpeed([3,6,7,11], 8))
```