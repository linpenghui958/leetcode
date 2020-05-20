```javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    const len = digits.length;
    for (let i = len - 1; i >= 0; i--) {
        let num = digits[i] + 1;
        if (num % 10 === 0) {
            digits[i] = 0; // 需要进位
        } else {
            digits[i] = num;  // 无需进位，结束
            break;
        }
    }

    const isAllZero = digits.every(i => i===0); // 全进位，需要增加一位情况
    if (isAllZero) {
        digits.unshift(1)
    }
    return digits;
};
```
考虑是否需要进位，以及刚好全是进位，需要增加一位的情况