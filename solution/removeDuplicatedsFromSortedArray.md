```javascript
var removeDuplicates = function(nums) {
    let tmpNum = nums[0];
    let count = 1;
    for (let i = 0; i < nums.length; i++) {
        if (nums[count-1] !== nums[i]) {
            nums[count++] = nums[i]
        }
    }
    return count;
};
```

先实现需要额外数组的情况，再简化
```javascript
var removeDuplicates = function(nums) {
    let tmpNum = nums[0];
    let count = 1;
    let res = []
    for (let i = 0; i < nums.length; i++) {
        if (res[res.length - 1]  !== nums[i]) {
            res.push(nums[i])
            count++
        }
    }
    return count
};
```