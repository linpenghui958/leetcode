```javascript
/**
 * @param {character[]} letters
 * @param {character} target
 * @return {character}
 */
var nextGreatestLetter = function(letters, target) {
  let asciiT = target.charCodeAt(0);
  let left = 0;
  let right = letters.length - 1;
  while(left <= right) {
    let mid = Math.floor((right + left) / 2);
    if (letters[mid] === target) {
      left = mid+1;
    } else if (letters[mid].charCodeAt(0) > asciiT) {
      right = mid-1;
    } else if (letters[mid].charCodeAt(0) <= asciiT) {
      left = mid+1;
    }
  }
  if (left > letters.length-1) return letters[0];
  return letters[left];
};
```