最长回文子串
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  // dp[i][j] 为从 位置i 到位置j是否为回文字
  // bad case dp[i][i] 为true
  // 状态转移方程 if s[i]===s[j] && dp[i+1][j-1] === true
  // 则dp[i][j] = true
  // bad case j=i, 长度为1，dp[i][j] = true;
  if (s.length === 0 ) return '';
  let res = '';
  const n = s.length;
  const dp = new Array(n);
  for (let i = 0; i < n; i++) {
    dp[i] = new Array(n)
  }
  console.log(dp);
  for (let i = n - 1; i >= 0; i--) {
    for (let j = i; j < n; j++) {
      // bad case
      if (j - i === 0) {
        dp[i][j] = true;
      // bad case
      } else if (j - i === 1 && s[i] === s[j]) {
        dp[i][j] = true;
      } else if (s[i] === s[j] && dp[i+1][j-1] === true) {
        dp[i][j] = true;
      }
      // 如果长度更长，更新结果
      if (dp[i][j] && j - i + 1 > res.length) {
        res = s.substring(i, j+1);
      }
    }
  }
  
  return res;
}
```

```javascript
该方法只能求最长回文子串的长度
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  // dp[i][j] 在s[i..j]中最长回文字的长度
  // bad case i === j 时，长度为1 
  // i > j 时，长度为0
  const n = s.length;
  const dp = new Array(n);
  // 初始化bad case
  for (let i = 0; i < n; i++) {
    dp[i] = new Array(n).fill(0);
    dp[i][i] = 1;
  }
  // 反向遍历，保证正确的状态转移
  for (let i = n - 1; i >= 0; i--) {
    for (let j = i + 1; j < n; j++) {
      if (s[i] === s[j]) {
        dp[i][j] = dp[i+1][j-1] + 2;
      } else {
        dp[i][j] = Math.max(dp[i][j-1], dp[i+1][j])
      }
    }
  }
  return dp[0][n-1]
};
```