```javascript
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