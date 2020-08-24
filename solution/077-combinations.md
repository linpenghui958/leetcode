```javascript
/**
 * @param {number} n
 * @param {number} k
 * @return {number[][]}
 */
const combine = function(n, k) {
   // 初始化结果数组
    const res = []   
    // 初始化组合数组
    const subset = []
    // 进入 dfs，起始数字是1
    dfs(1)  

    // 定义 dfs 函数，入参是当前遍历到的数字
    function dfs(index) {
        if(subset.length === k) {
            res.push(subset.slice())
            return 
        }
        // 从当前数字的值开始，遍历 index-n 之间的所有数字
        for(let i=index;i<=n;i++) {
            // 这是当前数字存在于组合中的情况
            subset.push(i) 
            // 基于当前数字存在于组合中的情况，进一步 dfs
            dfs(i+1)
            // 这是当前数字不存在与组合中的情况
            subset.pop()
        }
    }
    // 返回结果数组
    return res 
};
```