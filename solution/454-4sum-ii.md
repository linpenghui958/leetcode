使用数组A保存nums1，和nums2相加的合
key是sum，value是出现的次数
使用数组B保存nums3，和nums4相加的合
key是sum，value是出现的次数
循环数组B，寻找target = 0 - B[index],在A中是否存在
存在的话count += A[target]

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @param {number[]} nums3
 * @param {number[]} nums4
 * @return {number}
 */
var fourSumCount = function(nums1, nums2, nums3, nums4) {
    let count = 0;
    let resA = [];
    for (let i of nums1) {
        for (let j of nums2) {
            let sum = i + j;
            if (resA[sum]) {
                resA[sum] = resA[sum] + 1;
            } else {
                resA[sum] = 1;
            }
        }
    }

    for (let i of nums3) {
        for (let j of nums4) {
            let sum = i + j;
            let target = 0 - sum;
            if (resA[target]) {
                count += resA[target];
            }
        }
    }
    return count;
};
```