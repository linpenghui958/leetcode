```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let map = {}
    let length = nums.length;
    for (let i = 0; i < length; i++) {
        let searchVal = target - nums[i];
        if (Number.isInteger(map[searchVal])) {
            return [map[searchVal], i]
            break;
        } else {
          map[nums[i]] = i;
        }
    }
    return result;
};
```