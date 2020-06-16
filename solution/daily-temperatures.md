```javascript
/**
 * @param {number[]} T
 * @return {number[]}
 */
var dailyTemperatures = function(T) {
    let res = new Array(T.length).fill(0);
    let s = []; // 维护一个最大单调栈
    for (let i = 0; i < T.length; i++) {
        while( s.length > 0 && T[s[s.length - 1]] < T[i]) { // 如果s栈顶的值还要小于当前温度，则代表找到结果
            let topIndex = s.pop();
            res[topIndex] = i - topIndex; // 保存结果
        }
        s.push(i); // 保存下标，方便后面计算天数
    }
    return res;
};
```