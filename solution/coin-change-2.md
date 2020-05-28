```javascript
/**
 * @param {number} amount
 * @param {number[]} coins
 * @return {number}
 */
var change = function(amount, coins) {
    if(amount === 0) return 1;
    const dp = [new Array(amount + 1).fill(0)] // 初始化，使用0枚硬币，无法凑出金额，结果都为0
    // 从1开始比较方便运算
    for (let i = 1; i <= coins.length; i++) {
      dp[i] = new Array(amount + 1).fill(1);
      for (let j = 1; j <= amount; j++) {
        if (j - coins[i-1] >= 0) { // 目标金额大于当前硬币
          dp[i][j] = dp[i-1][j] + dp[i][j-coins[i-1]]
        } else {
          dp[i][j] = dp[i-1][j] // 否则直接沿用之前的最佳结果
        }
      }
    }
    return dp[coins.length][amount]
};
```
i为硬币的数量 j为需要凑齐的金额
dp[i][j] 为使用i枚硬币，凑齐j金额所需要的最小硬币数量