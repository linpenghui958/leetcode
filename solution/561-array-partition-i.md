```javascript
// min数对必是有序数列上相邻元素的证明
/**
 * @param {number[]} nums
 * @return {number}
 */
var arrayPairSum = function(nums) {
    nums = nums.sort((a,b) => a - b);
    let res = 0;
    for(let i = 0; i < nums.length; i+=2) {
        res += nums[i];
    }
    return res;
};
```