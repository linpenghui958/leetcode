```javascript
/**
 * @param {number[]} nums
 */
var Solution = function(nums) {
    this.data = nums;
};

/** 
 * @param {number} target
 * @return {number}
 */
Solution.prototype.pick = function(target) {
    let arr = []
    for (let i = 0; i < this.data.length; i++) {
        if (target == this.data[i]) {
            arr.push(i)
        }
    }
    return arr[Math.floor(Math.random() * arr.length)]
};

```