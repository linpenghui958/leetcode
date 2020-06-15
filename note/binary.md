#### 二分查找笔记

目标对象为数组

1. 终止条件

  > 例如 while(left <= right) 范围 [left, right] 终止条件为 left = right + 1; 
  > 终止时，区间为 [right + 1, right] 范围内没有元素
  > 例如 while(left < right) 范围 [left, right) 终止条件为 left == right;
  > 终止时，区间为 [right, right)

2. 收缩左右边界

  - 查找某个值

    > 终止条件 while(left <= right) 中间下标为mid
    > 若 nums[mid] > target , 则区间调整为 [left, mid - 1] , 所以 right = mid - 1;
    > 若 nums[mid] < target , 则区间调整为 [mid + 1, right], 所以 left = mid + 1;
    > 若 nums[mid] === target , 返回结果；
  
  - 查找左边界， 例如 nums: [1,2,2,2,3] target 2 , result 1, 数组nums中比target 2小的有 1 个

    > 终止条件 while(left < right), 查找区间 [left, right)
    > 若 nums[mid] > target , 则区间调整为 [left, mid), 所以 right = mid;
    > 若 nums[mid] < target , 则区间调整为 [mid, right), 所以 left = mid + 1;
    > 若 nums[mid] = target , 继续收缩右边界，向左靠近，所以 right = mid;
    > 最终终止条件 left === right, 既范围 [left, right)

  - 查找有边界， 例如 nums: [1,3,6,7,10] target 7 

    > 终止条件 while(left < right), 查找区间 [left, right)
    > 若 nums[mid] > target , 同上
    > 若 nums[mid] < target , 同上
    > 若 nums[mid] = target , 继续收缩左边界 , 所以 left = mid + 1;