```javascript
/**
 * @param {number[][]} envelopes (w, h)
 * @return {number}
 */
var maxEnvelopes = function(envelopes) {
  // 这个解法的关键在于，对于宽度 w 相同的数对，要对其高度 h 进行降序排序。因为两个宽度相同的信封不能相互包含的，逆序排序保证在 w 相同的数对中最多只选取一个。
  envelopes.sort((a,b) => a[0] === b[0] ? b[1] - a[1] : a[0]-b[0]);
  const len = envelopes.length;
  const dp = new Array(len).fill(1);
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < i; j++) {
      if (envelopes[i][1] > envelopes[j][1]) {
        dp[i] = Math.max(dp[i], dp[j] + 1); 
      }
    }
  }
  return Math.max(...dp);
};
```