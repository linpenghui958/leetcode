```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
    let result = []
    function backtrack(res = []) {
        if (res.length === nums.length) {
            result.push([...res]);
            return;
        }
        for(let i = 0; i < nums.length; i++) {
            if (res.includes(nums[i])) { // 不合理的情况跳过
                continue;
            }
            res.push(nums[i]); // 选择
            backtrack(res);  // 进入下一次选择
            res.pop(); // 取消选择
        }
    }
    backtrack();
    return result;
};
```