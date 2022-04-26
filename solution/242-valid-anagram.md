使用一个数组保存字母的个数
循环两个字符串
如果最终数组内没有多余的字母个数，则为有效字母异位词

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    let arr = [];
    for (let i = 0; i < s.length; i++) {
        let codeASC = s[i].charCodeAt();
        if (arr[codeASC]) {
            arr[codeASC] = arr[codeASC] + 1;
        } else {
            arr[codeASC] = 1;
        }
    }
    for (let i = 0; i < t.length; i++) {
        let codeASC = t[i].charCodeAt();
        if (arr[codeASC]) {
            arr[codeASC] = arr[codeASC] - 1;
        } else {
            arr[codeASC] = -1;
        }
    }
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] > 0 || arr[i] < 0) {
            return false;
        }
    }
    return true;
};
```