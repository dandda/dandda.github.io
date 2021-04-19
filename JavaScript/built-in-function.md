##### js 原生函数

1.Boolean()

> 过滤有空字符的字符串

```js
var str = "some,list,,of,values";
var arr = str.split(",");
arr.filter(Boolean);
```
