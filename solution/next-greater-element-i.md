```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var nextGreaterElement = function(nums1, nums2) {
    var obj = {}
    var minStack = [];
    var res = [];
    for (let i = 0; i < nums2.length; i++) {
        while(minStack.length >= 0 && minStack[minStack.length - 1] < nums2[i]) {
            obj[minStack.pop()] = nums2[i]
        }
        minStack.push(nums2[i])
    }
    for (let i = 0; i < nums1.length; i++) {
        var num = nums1[i];
        res.push(obj[num] ? obj[num] : -1)
    }
    return res;
};
```