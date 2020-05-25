```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {string}
 */
var minWindow = function(s, t) {
  const need = {}; // 需要收集的字符
  let needTypes = 0;
  for (let i of t) {
    if (need[i]) {
      need[i] += 1;
    } else {
      need[i] = 1;
    }
  }
  needTypes = Object.keys(need).length; // 当前缺失字符的种类数
  let left = 0;
  let right = 0;
  let start = 0, len = Infinity; // 记录起始位置，和字符串长度
 
  while(right < s.length) {
    let char = s[right];
    right++; // 这里从1开始的
    if (need[char] !== undefined) need[char]--; // 目标字符，类型-1
    if (need[char] === 0) needTypes--; // 目标字符为空，满足该字符条件，种类-1
    while (needTypes === 0) { // 只要满足收集所有字符种类，就一直收缩左边界
      if (right - left < len) { // 判断条件直接right-left
        len = right - left;
        start = left;
      }
      let char = s[left];
      if (need[char] !== undefined) need[char]++; // 收缩左边界后，更新类型、种类状态
      if (need[char] > 0) needTypes++
      left++;
    }
  }
  
  
  if (len === Infinity) return "";
  return s.substring(start, start + len)
};
```