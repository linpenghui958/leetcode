```javascript
/**
 * @param {number} a
 * @param {number[]} b
 * @return {number}
 */
var base = 1137;
//  (a * b) % k = (a % k)(b % k) % k
// a^12 = a^2 * (a^1)^10
var superPow = function (a, b) {
  if (b.length === 0) return 1;
  const last = b.pop();
  const part1 = myPow(a, last);
  const part2 = myPow(superPow(a, b), 10);
  return (part1 * part2) % base;
}


var myPow = function(a, b) {
  a %= base;
  let res = 1;
  for (let i = 0; i < b; i++) {
    res = res % base;
  }
  return res;
};
```