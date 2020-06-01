```javascript
var longestCommonSubsequence = function(s1, s2) {
  // base case dp[0][j] = 0 , dp[i][0] = 0
  // 状态转义方程
  // 如果两个字符相等 s1[i] === s2[j] , dp[i][j] = d[i-1][j-1] + 1
  // 如果两个字符不相等 s1[i] !== s2[j] , dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1])
  dp = new Array(s1.length + 1);
  for (let i = 0; i <= s1.length; i++) {
    dp[i] = new Array(s1.length).fill(0)
  }
  for (let j = 0; j <= s2.length; j++) {
    dp[0][j] = 0
  }
  console.log(dp)
  for (let i = 1; i <= s1.length; i++) {
    for (let j = 1; j <= s2.length; j++) {
      if (s1[i-1] === s2[j-1]) {
        console.log(i ,j, s1[i], s2[j])
        dp[i][j] = dp[i-1][j-1] + 1;
      } else {
        dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1])
      }
    }
  }
  return dp[s1.length][s2.length]
};

暴力递归
var longestCommonSubsequence = function(s1, s2) {
  function dp (i,j) {
    if (i === -1 || j === -1) return 0;
    if (s1[i] === s2[j]) {
      return dp(i-1, j-1) + 1;
    } else {
      return Math.max(dp(i, j-1), dp(i-1, j))
    }
  }
  return dp(s1.length-1, s2.length-1)
};
```