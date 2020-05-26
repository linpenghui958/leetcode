```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
  const res = []
  const need = {};
  for (let i of p) {
    if(need[i]) {
      need[i]++
    } else {
      need[i] = 1;
    }
  }
  let needTypes = Object.keys(need).length;
  console.log(need, needTypes)
  let left = 0; let right = -1;
  while(right < s.length) {
    right++;
    let char = s[right];
    if (need[char] !== undefined) need[char]--;
    if (need[char] === 0) needTypes--;
    while(needTypes === 0) {
      if (right - left + 1 === p.length) {
        console.log(left)
        res.push(left)
      }
      let char = s[left];
      if (need[char] !== undefined) need[char]++;
      if (need[char] > 0) needTypes++;
      left++;
    }
  }
  return res;
};
```
给定一个字符串 s 和一个非空字符串 p，找到 s 中所有是 p 的字母异位词的子串，返回这些子串的起始索引。

字符串只包含小写英文字母，并且字符串 s 和 p 的长度都不超过 20100。

说明：

- 字母异位词指字母相同，但排列不同的字符串。
- 不考虑答案输出的顺序。

示例 1:
> 输入:
> s: "cbaebabacd" p: "abc"

> 输出:
> [0, 6]

> 解释:
> 起始索引等于 0 的子串是 "cba", 它是 "abc" 的字母异位词。
> 起始索引等于 6 的子串是 "bac", 它是 "abc" 的字母异位词。