```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsets = function(nums) {
    let result = [];
    function backtrack(numbers, startIndex, cur) {
        result.push([...cur]) // 保存结果
        for (let i = startIndex; i < numbers.length; i++) {
            cur.push(numbers[i]);
            backtrack(numbers, i + 1, cur); // 注意下一次决策的起始位置
            cur.pop();
        }
    }
    backtrack(nums, 0, []);
    return result;
};
```