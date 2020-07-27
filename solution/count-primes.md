```javascript

/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
  let isPrimes = new Array(n).fill(true);
  for (let i = 2; i < n; i++) {
  // for (let i = 2; i * i < n; i++) { 优化外循环
    if (isPrimes[i]) {
      for (let j = i * 2; j < n; j += i) {
      // for (let j = i * i; j < n; j += i) { 优化内循环
        isPrimes[j] = false;
      }
    }
  }
  console.log(isPrimes)
  let count = 0;
  for (let i = 2; i < n; i++) {
    if (isPrimes[i]) count++
  }
  return count;
};
```