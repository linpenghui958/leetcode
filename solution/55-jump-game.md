```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function(nums) {
    let n = nums.length;
    let farthest = 0; // 最远可以跳到
    for (let i = 0; i < n - 1; i++) {
        // 最远距离与当前位置可以跳到的距离，取最大值
        farthest = Math.max(farthest, i + nums[i]);
        // 如果最远距离小于当前位置，则无法继续后跳
        if (farthest <= i) return false;
    }
    return true;
};
```