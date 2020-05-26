```javascript
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
var checkInclusion = function(s1, s2) {
  const map = {}; // 需要收集的字符
  for(let i of s1) {
    if (map[i]) {
      map[i]++
    } else {
      map[i] = 1;
    }
  }
  let needTypes = Object.keys(map).length;// 当前缺失字符的种类数
  let left = 0,right = -1;
  while(right < s2.length) {
    let char = s2[right];
    right++;  // right为从零开始
    if (map[char] !== undefined) map[char]--;
    if (map[char] === 0) needTypes--;
    while(needTypes === 0) {
      if (right-left === s1.length) { // 如果满足条件，并且长度正好与目标字符串一致
        return true
      }
      let char = s2[left];
      if (map[char] !== undefined) map[char]++; // 收缩左边界后，更新类型、种类状态
      if (map[char] > 0) needTypes++;
      left++
    }
  }
  return false;
};
```