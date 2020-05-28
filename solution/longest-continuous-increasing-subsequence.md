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
```