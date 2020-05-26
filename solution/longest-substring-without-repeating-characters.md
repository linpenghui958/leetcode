```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  let left = 0, right = -1;
  let res = 0;
  let arr = [];
  
  while(right < s.length - 1) {
    right++;
    let char = s[right];
    let index = arr.indexOf(char)
    if (index >= 0) { // 如果已存在，删除该已存在字符及之前的部分
      arr.splice(0, index + 1)
    }
    arr.push(char);
    res =  Math.max(arr.length, res)
  }
  return res;
};
```