#### Array.apply()

```js
let arr = Array.apply(unll, new Array(5)); //[undefined, undefined, undefined, undefined, undefined]
// 通过apply相当于创建了长度为5的数组，且设置了初始值为undefined
let arr1 = new Array(5); //[empty × 5]
// 直接创建长度为5的数组，没有初始值。
```
