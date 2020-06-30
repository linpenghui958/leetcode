```javascript
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
    let sign = '+'; // 符号位暂存
    let num = 0;
    let stack = [];
    for(let i = 0; i < s.length; i++) {
      if (!Number.isNaN(Number(s[i])) && s[i] !== ' ') {
        num = 10*num + Number(s[i]); // 处理数字情况
      }
      if ((Number.isNaN(Number(s[i])) && s[i] !== '') || i === s.length - 1) { // 处理遇到符号位的情况
        let top = 0;
        switch(sign) {
          case '+':
            stack.push(+num);
            break;
          case '-':
            stack.push(-num);
            break;
          case '*':   // 乘除优先级高，先于当前数字结合
            top = stack.pop();
            stack.push(top*num);
            break;
          case "/":
            top = stack.pop();
            stack.push(parseInt(top/num));
            break;
        }
        sign = s[i];
        num = 0;
      }
    }
    return stack.reduce((res, cur) => res + cur, 0)
};
```