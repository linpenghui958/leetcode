```javascript
/**
 * initialize your data structure here.
 */
var MinStack = function() {
    this.stack = [];
    this.min_stack = [];
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
    this.stack.push(x);
    // 初始化 或 当有更小值入栈时，将当前值入最小栈中
    if(this.min_stack.length == 0 || this.min_stack[this.min_stack.length-1] >= x){
        this.min_stack.push(x);
    }
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
    // 当出栈值 == 当前最小值时，最小栈的值也要出栈
    if(this.stack.pop() == this.min_stack[this.min_stack.length-1]){
        this.min_stack.pop();
    }
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
    return this.stack[this.stack.length-1];
};

/**
 * @return {number}
 */
MinStack.prototype.getMin = function() {
    // 返回与当前基栈同步的最小栈的栈顶元素即为最小值
    return this.min_stack[this.min_stack.length-1];
};
```
