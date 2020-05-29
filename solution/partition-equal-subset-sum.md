```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canPartition = function(nums) {
  let sum = nums.reduce((res, cur) => res + cur, 0);
  if (sum % 2 !== 0) return false;
  const target = sum / 2;
  const len = nums.length;
  const dp = new Array(len);
  for (let i = 0; i <= len; i++) {
    dp[i] = new Array(target + 1).fill(false);
  }
  for (let i = 1; i <= nums.length; i++) {
    dp[i][0] = true; // bad case
    for (let j = 1; j <= target; j++) {
      if (j - nums[i - 1] >= 0) {
        dp[i][j] = dp[i-1][j]|| dp[i-1][j - nums[i - 1]];
      } else {
        dp[i][j] = dp[i-1][j]
      }
    }
  }
  return dp[nums.length][target]
};
```