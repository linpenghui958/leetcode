```javascript
/**
 * @param {number[][]} image
 * @param {number} sr
 * @param {number} sc
 * @param {number} newColor
 * @return {number[][]}
 */
var floodFill = function(image, sr, sc, newColor) {
    const oldColor = image[sr][sc]; // 记录初始颜色
    fill(image, sr, sc, newColor, oldColor);
    return image;
};

var fill = function (image, i, j, newColor, origColor) {
    if (!inArea(i, j, image)) return; // 不在边界内
    if (image[i][j] !== origColor) return; // 已经改过颜色了
    if (image[i][j] === -1) return; // 已经遍历过的，避免死循环
    image[i][j] = -1; // 记录遍历
    fill(image, i-1, j, newColor, origColor);
    fill(image, i+1, j, newColor, origColor);
    fill(image, i, j-1, newColor, origColor);
    fill(image, i, j+1, newColor, origColor);
    image[i][j] = newColor; // 最终改变颜色
}

var inArea = function(x, y, image) {
    return x >= 0 && x < image.length && y >= 0 && y < image[0].length;
}
```