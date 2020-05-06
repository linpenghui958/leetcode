```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var bracketMap = {
    '(': ')',
    '[': ']',
    '{': '}'
}
var isValid = function(s) {
    var arr = s.split('');
    var temp = [];
    let i = 0;
    let valid = true;
    while(i < arr.length) {
        if (bracketMap[arr[i]]) {
            temp.push(bracketMap[arr[i]])
        } else {
            if (temp.pop() !== arr[i]) {
                valid =false
            }
        }
        i++
    }
    return temp.length > 0 ? false : valid;
};
```
使用堆，匹配到左括号，进堆，然后依次出堆与右括号比较