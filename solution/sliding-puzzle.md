```javascript
/**
 * @param {number[][]} board
 * @return {number}
 */
var slidingPuzzle = function(board) {
    // 目标数组扁平化 [1,2,3,4,5,0]
    let start = "";
    let target = "123450"
    for (let i = 0; i < 2; i++) {
        for (let j = 0; j < 3; j++) {
            start += String(board[i][j])
        }
    }
    // 相邻位置map
    let neighbor = [
        [1,3],
        [0,4,2],
        [1,5],
        [0,4],
        [3,1,5],
        [4,2]
    ]
    // 转化为字符串
    const visted = new Set();
    const q = [];
    let setup = 0;
    q.push(start);
    while(q.length) {
        let size = q.length;
        for (let i = 0; i < size; i++) {
            let curr = q.shift();
            if (curr === target) {
                return setup;
            }
            for(let j = 0; j < curr.length; j++) {
                // 讲0与相邻换位
                if (curr[j] === '0') {
                    const swapArr = neighbor[j];
                    for (let k = 0; k < swapArr.length; k++) {
                        let newBoard = swap(curr, j, swapArr[k]);
                        // console.log('swap', j, swapArr[k] , newBoard, q)
                        // 避免遍历过的情况
                        if (!visted.has(newBoard)) {
                            q.push(newBoard);
                            visted.add(newBoard)
                        }
                    }
                }
            }
        }
        setup++
    }
    return -1;
};

function swap(string, i, j) {
    let tempArr = string.split('');
    [tempArr[i], tempArr[j]] = [tempArr[j], tempArr[i]];
    return tempArr.join('');
}

```