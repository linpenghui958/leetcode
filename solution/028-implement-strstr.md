```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    if (needle === '') return 0;
    let index = -1;
    for (let i = 0; i < haystack.length; i++) {
        if (haystack[i] === needle[0]) {
            let index = i;
            let flag = true;
            for (let j = 0;j < needle.length;j++) {
                if (haystack[i+j] !== needle[j]) {
                    index = -1;
                    flag = false;
                    break;
                }
            }
            if (flag) return index
        }
    }
    return index
}; 
```
KMP算法O(h+n)、BM算法O(h)、Sunday算法更优O(n)