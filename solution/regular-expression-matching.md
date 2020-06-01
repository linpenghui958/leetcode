```javascript
暴力递归
/**
 * @param {string} s
 * @param {string} p
 * @return {boolean}
 */
var isMatch = function (s, p) {
    if (!p) return !s;
    const first = (s[0] === p[0] || p[0] === '.') && !!s[0];
    if (p.length >= 2 && p[1] === '*') {
        return isMatch(s, p.substring(2)) || (first && isMatch(s.substring(1), p)); // 如果遇到*，匹配0次，则跳过p[2:]，匹配多次则右移string，继续匹配p
    }
    return first && isMatch(s.substring(1), p.substring(1)); // 默认匹配情况
}
// 优化添加memo缓存
```