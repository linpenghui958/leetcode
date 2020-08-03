```javascript
双指针方法
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isSubsequence = function(s, t) {
    let i = 0;
    let j = 0;
    while(i < s.length && j < t.length) {
      if (s[i] === t[j]) {
        i++;
        j++;
      } else {
        j++;
      }
    }
  return i===s.length;
};
```
二分查找方法，待填坑