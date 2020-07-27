```javascript
暴力递归解法
var minDistance = function(word1, word2) {
  const memo = new Map();
  function dp(i ,j) {
    if (i === -1) return j + 1;
    if (j === -1) return i + 1;
    if (word1[i] === word2[j]) {
      return dp(i - 1, j - 1);
    } else {
      return Math.min(
        dp(i, j-1) + 1,
        dp(i - 1, j) + 1,
        dp(i-1,j-1) + 1
      )
    }
  }
  return dp(word1.length - 1, word2.length - 1)
};
提交超时。添加一下备忘录
var minDistance = function(word1, word2) {
  const memo = new Map();
  function dp(i ,j) {
    const key = `i${i}-j${j}`;
    if (memo.has(key)) {
      return memo.get(key)
    }
    if (i === -1) return j + 1;
    if (j === -1) return i + 1;
    if (word1[i] === word2[j]) {
      memo.set(key, dp(i - 1, j - 1))
    } else {
      memo.set(key, Math.min(
        dp(i, j-1) + 1,
        dp(i - 1, j) + 1,
        dp(i-1,j-1) + 1
      ))
    }
    return memo.get(key)
  }
  return dp(word1.length - 1, word2.length - 1)
};
dptable自底向上解法
var minDistance = function(s1, s2) {
  // dp[i][j]  i为s1长度，j为s2长度，dp值
  // bad case i，j长度为零时
  const dp = new Array(s1.length + 1).fill([0]);
  
  for (let i = 1; i <= s1.length; i++) {
    dp[i] = [i];
  }
  for (let j = 1; j <= s2.length; j++) {
    dp[0][j] = j;
  }
  for (let i = 1; i <= s1.length; i++) {
    for (let j = 1; j <= s2.length; j++) {
      if (s1[i - 1] === s2[j - 1]) {
        dp[i][j] = dp[i-1][j-1] // 字符相等，则跳过，直接取dp[i-1][j-1]的值
      } else {
        dp[i][j] = Math.min(
          dp[i][j-1] + 1, // 插入，所以i保持原位，j继续往前
          dp[i-1][j-1] + 1, // 替换，所以i，j均前进
          dp[i-1][j] + 1, // 删除，所以i往前，j继续往前
        )
      }
    }
  }
  return dp[s1.length][s2.length]
}
```

