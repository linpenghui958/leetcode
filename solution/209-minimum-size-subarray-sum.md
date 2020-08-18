```javascript
双指针方法
/**
 * @param {number} s
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function(s, nums) {
  let left = 0, right = 0, res = Infinity;
  let sum = 0;
  while(right < nums.length) {
    sum += nums[right];
    while(sum >= s) { // 满足条件情况
      let len = right - left + 1;
      res = Math.min(res, len);
      sum -= nums[left++]; // 收缩左边界
    }
    right++;
  }
    return res === Infinity ? 0 : res;
};
```