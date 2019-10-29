##### 利用`Math.max()`方法获取数组中最大值

```javascript
function jerkMax(arr_obj) {
  return Math.max.apply(null, arr_obj);
}
// 只能传入纯数字或者数字字符串的数组。
let arr = [2, 3, 4, 10, 7, 98];
let num = jerkMax(arr);
console.log(num);

let arr1 = ["1", "2", "11", "15", "3"];
console.log(jerkMax(arr1)); //15
```

##### 如何让 html 页面自动刷新

1. js,setTimeout()
2. 在 html 页面的 head 部分添加 meta 信息。

```html
<!--content 表示时间间隔，30表示每隔30秒刷新一次 -->
<meta http-eqiv="refresh" content="30" />
```

---

- - \* \* \* \* === - - \* \* \* \* ===== - - \* \* \* \* ===== - - \* \* \* \* ====== - - \* \* \* \*

分割线，以下不是技巧

##### jq 页面传值

a 页面:

```html
<div onclick="send(id)"></div>
```

```javascript
function send(id) {
  let url = "index.html" + "?id=" + encodeURI(id);
}
window.location.href = url;
```

b 页面:

```javascript
let url = location.search;
if (url.indexOf("?") != -1) {
  let str = url.substr(1);
}
```

##### jq 实时监听输入框的值

```javascript
$("input").bind("input propertychange", function() {});
```
