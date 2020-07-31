```javascript
动态规划、暴力递归解决
/**
 * @param {number[]} nums
 * @return {number}
 */
const memo = [];
var jump = function(nums) {
    // dp[nums][i] 从位置i，跳到最后一格，至少需要多少步
    // 最终需要的结果为 dp[nums][0] 从0跳到最后一格，最少需要多少步
    // bad case i >= nums.length - 1时 ,在最后一格位置，或者超出nums长度，不需要跳，0步
    for (let i = 0; i < nums.length; i++) {
        memo[i] = nums.length; // 初始化 为n，相当于INFINITY
    }
    return dp(nums, 0);
};

var dp = function (nums, p) {
    let n = nums.length;
    // bad case 位置p已经在结果，或者超出nums长度
    if (p >= n - 1) {
        return 0;
    }
    // 如果计算过，直接返回
    if (memo[p] !== n) {
        return memo[p];
    }
    // 当前位置可以前进的步数
    let step = nums[p];
    // 循环得到最优结果
    for (let i = 1; i <= step; i++) {
        // 位置p，前进i步，即p+i位置的最优解
        let subProblem = dp(nums, p + i);
        // 当前最优解memo[p]，和前进一次（所以是subProblem+1），p+i位置的最优解，取最小值
        memo[p] = Math.min(memo[p], subProblem + 1)
    }
    return memo[p];
}

贪心算法

var jump = function(nums) {
    let futherest = 0;
    let end = 0;
    let n = nums.length;
    let jump = 0;
    for (let i = 0; i < n-1; i++) {
        // 当前位置能跳到的最远位置
        futherest = Math.max(futherest, nums[i] + i);
        // 如果end即最远位置到了，更新步数和end
        if (end === i) {
            jump++;
            end = futherest;
        }
    }
    return jump;
}
```