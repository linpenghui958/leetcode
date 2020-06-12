```javascript
function backtrack(left, right, track, res) {
  if (right < left) return;
  if (left < 0 || right < 0) return;
  if (left === 0 && right === 0) {
    res.push(track.join(''));
  }
  
  track.push('(');
  backtrack(left - 1, right, track, res);
  track.pop();

  track.push(')');
  backtrack(left, right - 1, track, res);
  track.pop();
}
// 条件1 一个「合法」括号组合的左括号数量一定等于右括号数量
// 条件2 当 0 <= i < n时，左括号数量大于右括号，所以剩下的right > left
// 记录left、right
// 左括号要比右括号多
// 尝试放一个左括号，尝试放一个右括号

/**
 * @param {number} n
 * @return {string[]}
 */
function generateParenthesis(n) {
  let res = [];
  let track = [];
  backtrack(n, n, track, res);
  console.log(res)
  return res;
}

```