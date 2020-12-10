> indexOf

```javascript
let arr = [14, 27, 7, 27, 1, 6, 5, 5];
let newArr = [];
for (let i = 0; i < arr.length; i++) {
  // 新数组有没有这元素，没有就放进去。-1表示没这个元素。
  if (newArr.indexOf(arr[i]) === -1) {
    newArr.push(arr[i]);
  }
}
```

> new Set()

```javascript
let arr = [14, 27, 7, 27, 1, 6, 5, 5];
// 新数据结构Set，类似于数组，但成员值不重复
let newArr = [...new Set(arr)];
// or
let newArr = Array.from(new Set(arr));
```

> filter

```javascript
let arr = [14, 27, 7, 27, 1, 6, 5, 5];
let newArr = arr.filter((item, index) => {
  // indexOf每次从14开始找，找到的元素第一次出现时的下标。所以27的下标一直是1.
  return arr.indexOf(item) === index;
});
```
