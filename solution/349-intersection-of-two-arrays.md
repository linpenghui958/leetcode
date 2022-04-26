
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    const set = new Set();
    const res = [];
    for(let i of nums1) {
        set.add(i)
    }
    for(let i of nums2) {
        if (set.has(i) && res.indexOf(i) < 0) {
            res.push(i)
        }
    }
    return res;
};
```