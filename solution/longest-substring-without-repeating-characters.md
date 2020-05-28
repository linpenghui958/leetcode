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

滑动窗口套路

/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  let left = 0, right = 0;
  let res = 0;
  let map = {};
  
  while(right < s.length) {
    let char = s[right];
    right++;
    if (!map[char]) {
      map[char] = 1
    } else {
      map[char]++
    }
    while(Object.values(map).filter(i => i > 1).length > 0) {
      let char = s[left];
      left++;
      if (map[char]) map[char]--
    }
    res = Math.max(res, right - left)
  }
  return res;
};
```