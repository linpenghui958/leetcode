```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    // 方法1
    // return s.trim().split(/\s+/).reverse().join(' ');
    
    // 方法2
    s = s.trim();
    let res = [];
    let curr = '';
    for (let j = s.length - 1; j >= -1; j--) {
        if (s[j] === undefined || s[j] === ' ') {
            curr.length > 0 && res.push(curr);
            curr = '';
        } else {
            curr = s[j] + curr;
        }
    }
    return res.join(' ')
};
```