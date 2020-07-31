```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function(height) {
    // 暴力解法
    let n = height.length;
    const dp = new Array(n).fill(0);
    // 循环求出每个位置可以接的雨水
    for (let i = 0; i < n; i++) {
        // 该位置左边最大和右边最大，然后取min减去当前i的高度。即为可接雨水数目
        const leftMax = Math.max(...height.slice(0,i));
        const rightMax = Math.max(...height.slice(i + 1, n));
        const min = Math.min(leftMax, rightMax);
        if (min > 0) {
            dp[i] = min - height[i] > 0 ? min - height[i] : 0
        }
    }
    return dp.reduce((sum, cur) => sum + cur, 0);
};

var trap = function(height) {
    // 双指针
    if(height.length === 0) return 0;
    const n = height.length;
    let ans = 0;
    // 左边界、右边距
    let left = 0;
    let right = n - 1;
    // 左边当前最高值、右边当前最高的值
    let l_max = height[0];
    let r_max = height[n-1];
    while(left < right) { // 终止条件left = right
        l_max = Math.max(l_max, height[left]);
        r_max = Math.max(r_max, height[right]);
        // 取l_max、r_max中小的值
        if (l_max < r_max) {
            ans += l_max - height[left];
            left++;
        } else {
            ans += r_max - height[right];
            right--;
        }
    }
    return ans;
};
```