```javascript
var stoneGameII = function(piles) {
	let len = piles.length;
	const dp = new Array(len);
	// 初始化dp
	for (let i = 0; i <= len; i++) {
		dp[i] = []
		for (let j = 0; j <= len; j++) {
			dp[i][j] = [0,0]
		}
	}
	// bad case
	for (let i = 0; i <= len; i++) {
		dp[i][i][0] = piles[i];
		dp[i][i][1] = 0;
	}
	// 循环求解
	for (let l = 2; l <= len; l++) { // 数组长度
		for (let i = 0; i <= len - l; i++) { // 起点i
			let j = i + l - 1;  // 终点j
			let left = piles[i] + dp[i+1][j][1];
			let right = piles[j] + dp[i][j-1][1];
			if (left > right) {
				dp[i][j][0] = left;
				dp[i][j][1] = dp[i+1][j][0];
			} else {
				dp[i][j][0] = right;
				dp[i][j][1] = dp[i][j-1][0];
			}
		}
	}
	return res[0] - res[1];
};

// dp[i][j] = [fir, sec] 从piles的i到j，先选fir和后选sec的最优结果
// bad case dp[i][i] = [piles[i], 0] 起始都在同一个位置，即石头堆仅一个选择
// 状态转移方程
// 起点i 终点j
// 如果选择最右边 dp[i][j][0] = piles[i] + dp[i+1][j][1] 当前选择 + 上一次的选择（上一次的sec）
// 如果选择最左边 dp[i][j][0] = piles[j] + dp[i][j-1][1] 
// 选择右边，后选sec的值为
// dp[i][j][1] = dp[i+1][j][0]
// 斜着遍历顺序 
// for (let len = 2; len <= piles.length; len++) {} 石碓的长度。即i到j长度
// len 长度为1的bad case已经初始化，所以从长度为2开始遍历
//  for ( let i = 0; i <= piles.length - len; i++) 起点i从0开始
// 		j = i + len - 1;
```