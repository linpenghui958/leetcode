```javascript
复杂度N*N，使用动态规划，暴力解
/**
 * @param {number[]} nums
 * @return {number}
 */
var findNumberOfLIS = function(nums) {
  const dp = new Array(nums.length).fill(1);
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < i; j++) {
      if (nums[i] > nums[j]) {
        dp[i] = Math.max(dp[i], dp[j] + 1)
      }
    }
  }
  let res = 0;
  for (let i = 0; i < dp.length; i++) {
    res = Math.max(res, dp[i])
  }
  return res;
}


复杂度NlogN，使用二分查找
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
    const top = []; // 牌堆的数字
    let level = 0; // 层级

    for (let i = 0; i < nums.length; i++) {
        const cur = nums[i];

        let left = 0, right = level;
        while(left < right) {
            const mid = Math.floor((right + left) / 2);
            if (top[mid] > cur) {
                right = mid;
            } else if (top[mid] < cur) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        if (left === level) level++; // 如果没找到，新建一个牌堆，层级+1
        top[left] = cur; // 替换该牌堆最上卡片
    }
    return level; // 返回层级
};
```