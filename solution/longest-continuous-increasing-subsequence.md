```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLengthOfLCIS = function(nums) {
  let left = 0 ,right = 0;
  let len = nums.length;
  let res = 0;
  while(right < len) {
    const curNum = nums[right];
    right++;
    res = Math.max(res, right - left); // 更新最大值
    if(nums[right] <= curNum) { // 连续递增序列破坏，则更新左下标
      left = right;
    }
  }
  return res;
};

动态规划解法
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
  const len = nums.length;
  if (len === 0) return 0;
  // badcase 
  const dp = new Array(len).fill(1);
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < i; j++) {
      const curr = nums[i];
      if (curr > nums[j]) {
        // 状态转移方程
        dp[i] = Math.max(dp[i], dp[j] + 1);
      }
    }
  }
  return Math.max(...dp);
};
```