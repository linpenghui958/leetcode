```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
    let result = []
    function backtrack(res = []) {
        if (res.length === nums.length) {
            result.push([...res]);
            return;
        }
        for(let i = 0; i < nums.length; i++) {
            if (res.includes(nums[i])) { // 不合理的情况跳过
                continue;
            }
            res.push(nums[i]); // 选择
            backtrack(res);  // 进入下一次选择
            res.pop(); // 取消选择
        }
    }
    backtrack();
    return result;
};

// dfs 情况
const permute = function(nums) {
  const len = nums.length;
  const cur = [];
  const visited = new Set();
  const res = [];
  
  function dfs(nth){
    if (nth === len) {
      res.push([...cur]);
      return;
    }
    for (let i = 0; i < len; i++) {
      if (!visited.has(nums[i])) {
        cur.push(nums[i]);
        visited.add(nums[i]);
        dfs(nth+1);
        cur.pop();
        visited.delete(nums[i])
      }
    }
  }
  dfs(0);
  return res;
}
```