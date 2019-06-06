# npm-模块打卡记录

2019.06.06记录：   

1.is-sorted模块——用来检查数组是否已排序

``` javascript
function defaultComparator (a, b) {
  return a - b
}

module.exports = function checksort (array, comparator) {
    //判断是否是数组
  if (!Array.isArray(array)) throw new TypeError('Expected Array, got ' + (typeof array))
    //判断排序的方法是自带的还是自定义的
  comparator = comparator || defaultComparator


  for (var i = 1, length = array.length; i < length; ++i) {
    //遍历数组，如果其中有相邻的值相减大于0，则说明此排序是错误的，返回false
    if (comparator(array[i - 1], array[i]) > 0) return false
 
  }

  return true
}

```

``` javascript
//使用方法
var sorted = require('is-sorted')

console.log(sorted([1, 2, 3]))
// => true

console.log(sorted([3, 1, 2]))
// => false

// 
console.log(sorted([3, 2, 1], function (a, b) { return b - a }))
// => true
```
---