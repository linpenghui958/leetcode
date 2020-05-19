```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
    let end = s.length - 1;
    while(end > 0 && s[end] == ' ') {
        end--;
    }
    if (end < 0) return 0;
    let start = end;
    while(start >= 0 && s[start] != ' ') {
        start--;
    }
    return end - start;
};
```
从后往前遍历，先排除空格，找到结尾的下标end，然后往前，找到下一个空格的下标start