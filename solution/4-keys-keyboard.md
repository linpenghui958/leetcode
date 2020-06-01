```javascript
暴力递归
var maxA = function (N) {
  function dp(n, a_num, copy) {
    if (n <= 0) return a_num;
    return Math.max(
      dp(n - 1, a_num + 1, 0), // 按下 A
      dp(n - 1, a_num + copy, copy), // 按下 ctrl + v
      dp(n - 2, a_num, a_num) // 按下 ctrl + a 和 ctrl + c
    )
  }
  return dp(N, 0, 0);
}

var maxA = function (N) {
    const dp = [];
    dp[0] = 0;
    for (let i = 1; i <= N; i++) {
        dp[i] = dp[i-1] + 1;
        for (let j = 2; j < i; j++) {
            dp[i] = Math.max(dp[i], dp[j-2] * ( i - j + 1)) // 按a和按ctrl+v比较
        }
    }
    return dp[N]
}
```