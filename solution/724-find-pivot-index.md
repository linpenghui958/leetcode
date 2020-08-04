```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var pivotIndex = function(nums) {
  // 不包括中间数本身
  let sum = [];
  let n = nums.length;
  sum[0] = nums[0];
  // 求出每个位置的合
  for (let i = 1; i < nums.length; i++){
    sum[i] = sum[i-1] + nums[i];
  }
  for (let i = 0; i < sum.length; i++) {
    // 例如 i = 3;
    // leftSum = sum[2] // sum[i-1]
    // rightSum = sum[5] - sum[3] // sum[n-1] - sum[i]
    // 比较当前位置，左右两边位置的合
    let leftSum = sum[i-1] || 0;
    let rightSum = sum[n-1] - sum[i];
    if (leftSum === rightSum) {
      return i;
    }
  }
  return -1;
};
```
可以只保留一个总和sum
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var pivotIndex = function(nums) {
  // 不包括中间数本身
  let sum = nums.reduce((val, cur) => val += cur, 0)
  let leftSum = 0;
  for (let i = 0; i < nums.length; i++) {
    if (leftSum === sum - leftSum - nums[i]){
      return i;
    }
    leftSum += nums[i];
  }
  return -1;
};
```