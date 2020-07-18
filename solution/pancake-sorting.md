```javascript
/**
 * @param {number[]} A
 * @return {number[]}
 */

let res = [];
var pancakeSort = function(A) {
  let ans = [];
  let max;
  while(A.length > 1) {
    max = getMaxIndex(A);
    max > 0 && (ans.push(max+1));
    reverse(A, 0, max);
    reverse(A, 0, A.length-1);
    ans.push(A.length);
    A.pop();
  }
  return ans;
};
//获取一个数组最大值的下标
function getMaxIndex(nums){
    let max = 0;
    for(let i=0;i<nums.length;i++){
        if(nums[i]>nums[max]){
            max = i;
        }
    }
    return max;
}

var reverse = function (arr, i, j) {
   while (i < j) {
        temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++; j--;
    }
}
```