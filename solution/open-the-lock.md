```javascript
function plusOne(s, j) {
  let arr = s.split('');
  if (arr[j] === '9') {
     arr[j] = '0';
  } else {
    arr[j] = String(Number(arr[j]) + 1)
  }
  return arr.join('');
}
function minusOne(s, j) {
  let arr = s.split('');
  if (arr[j] === '0') {
     arr[j] = '9';
  } else {
    arr[j] = String(Number(arr[j]) - 1)
  }
  return arr.join('');
}
/**
 * @param {string[]} deadends
 * @param {string} target
 * @return {number}
 */
var openLock = function(deadends, target) {
  const arr = ['0000'];
  const visited = new Set(); 
  const dead = new Set();
  let step = 0;
  for (let i of deadends) {
    dead.add(i)
  }
  while(arr.length) {
    const size = arr.length;
    for (let i = 0; i < size; i++) {
      let cur = arr.shift();
      if (dead.has(cur)) {
        continue;
      }
      if (cur === target) {
        return step;
      }
      for (let j = 0; j < 4; j++) {
        const up = plusOne(cur, j);
        const down = minusOne(cur, j);
        if (!visited.has(up)) {
          arr.push(up);
          visited.add(up);
        }
        if (!visited.has(down)) {
          arr.push(down);
          visited.add(down);
        }
      }
    }
    step++
  }
  return -1;
};

```