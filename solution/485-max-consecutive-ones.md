```javascript
遍历方法
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    let res = 0;
    const target = 1;
    let result = 0;
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === target) {
            res+=1;
        } else {
            res = 0;
        }
        result = Math.max(res, result);
    }
    return result;
};
双指针方法
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    let slow = 0, fast = 0, res = 0;
    const target = 1;
    let result = 0;
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === target) {
            fast++;
            res = fast - slow;
        } else {
            slow = i;
            fast = i;
        }
        result = Math.max(res, result);
    }
    return result;
};
```