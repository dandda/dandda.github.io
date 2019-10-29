```javascript
let item = {
  name: "chuchu",
  node: 1
};
let form = [];
for (let i = 0; i < 3; i++) {
  form.push(item);
}
//这里我只想改数组的第一项，结果数组的每项都被改变，是因为数组的每个item都指向同一个堆。
form[0].name = "Lala";
console.log(form);
// [
//   {
//     name:'Lala',
//     node:1
//   },
//   {
//     name:'Lala',
//     node:1
//   },
//   {
//     name:'Lala',
//     node:1
//   }
// ]
```

**解决方法一**

```javascript
let item = {
  name: "chuchu",
  node: 1
};
let form = [];
for (let i = 0; i < 3; i++) {
  // 对 item进行深复制
  let new_item = JSON.parse(JSON.stringify(item));
  form.push(new_item);
}
form[0].name = "DD";
console.log(form);
[
  {
    name: "DD",
    node: 1
  },
  {
    name: "chuchu",
    node: 1
  },
  {
    name: "chuchu",
    node: 1
  }
];
```

**解决方法二**

```javascript
let form = [];
for (let i = 0; i < 3; i++) {
  // 之前 item 是在循环外定义的，所以 item 的内存地址不曾变过，循环出来的 item 自然都是指向同一个内存地址。
  //现在 item 放在了循环内，每次循环都新建了一个 item 对象，所以就不会出问题了。
  let item = {
    name: "chuchu",
    node: 1
  };
  form.push(item);
}
form[1].name = "TT";
console.log(form);
// [
//   {
//     name: "chuchu",
//     node: 1
//   },
//   {
//     name: "TT",
//     node: 1
//   },
//   {
//     name: "chuchu",
//     node: 1
//   }
// ];
```

> 我以为我了解 引用类型数据，然后还是太天真，遇到实际运用，还是不会用。
