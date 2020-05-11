```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
 // 暴力解 复杂度O(N)
var searchInsert = function(nums, target) {
    let resIndex = -1;
    for (let i = 0;i < nums.length; i++) {
        let currentVal = nums[i];
        let nextVal = nums[i+1];
        if (currentVal > target && i === 0) {
            resIndex = 0;
        } else if (currentVal === target) {
            resIndex = i;
        } else if (currentVal < target && nextVal > target || currentVal < target && i === nums.length - 1) {
            resIndex = i + 1;
        } 
    }
    return resIndex;
};

// 二分查找 复杂度O(logN)
var searchInsert = function(nums, target) {
    let len = nums.length;
    if (len === 0) return 0;
    if (target < nums[0]) return 0;
    if (target > nums[len - 1]) return len;

    let left = 0;
    let right = len - 1;

    while(left < right) {
        let mid = Math.floor(left + (right - left) / 2);
        if (nums[mid] < target) {
            left = mid + 1;  
        } else {
            right = mid;
        }
    }
    return left;
};

```