如果sum出现重复的，则不为快乐数
否则循环，直到找到sum=1的情况

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
    if (n <= 0 ) return false;
    let set = new Set();
    let num = n;

    while(true) {
        let arr = num.toString().split('');
        let sum = 0;
        for (let i of arr) {
            sum = sum + (i*i);
        }
        if (sum === 1) return true;
        if (set.has(sum)) {
            return false;
        } else {
            set.add(sum);
            num = sum;
        }
    }
};
```