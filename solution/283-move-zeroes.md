```javascript
双指针方法
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
  let lastNotZeroIndex = 0;
  // 将不是0的数依次赋值
  for(let i = 0; i < nums.length; i++) {
    if (nums[i] !== 0) {
      nums[lastNotZeroIndex++] = nums[i];
    }
  }
  // 剩下的全部填0
  for (let i = lastNotZeroIndex; i < nums.length; i++) {
    nums[i] = 0;
  }
};
```