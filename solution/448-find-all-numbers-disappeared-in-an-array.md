```javascript
// 智障版
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    const map = [];
    let res = [];
    // 循环标记
    for (let i = 0; i < nums.length; i++) {
        if (!map[nums[i] - 1]) {
            map[nums[i] - 1] = nums[i];
        }
    }
    // 空的即为没有出现的数字
    for (let i = 0; i < nums.length; i++) {
        if (!map[i]) {
            res.push(i+1)
        }
    }
    return res;
};

// 不使用额外空间版
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    let res = [];
    // 以下标来区分，将数组中mums[i]置为负数，找出最后数组中为整数的位置i，未出现的数字为i+1
    // 转换前[ 2, 1,1, 4, 5]
    // 转换后[-2,-1,1,-4,-5]
    // 位置2的值依然为正数，表示2+1，即3没有出现过
    for (let i = 0; i < nums.length; i++) {
        let index = Math.abs(nums[i]) - 1;
        nums[index] = -Math.abs(nums[index])
    }
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] > 0) {
            res.push(i+1);
        }
    }
    return res;
};
```