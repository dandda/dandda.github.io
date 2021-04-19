#### localStorage and sessionStorage

相对新的 API，api 和功能基本相同,都不参与和服务器的通信大小一般在 5M 左右。

区别在于持久性：sessionStorage（仅在浏览器会话窗口里可用，关闭浏览器窗口或选项卡就会移除）,但是重新加载页面和宿刷新一样有效。
localstorage:存储时间永久(用户不主动删除)，在所有同源窗口中都是共享的。
都非常适合在页面之间的客户端脚本中持久存储所需的非敏感数据。

#### cookie:

1.通常，cookie 用于存储身份验证，会话和广告跟踪的标识令牌。

2.存储时间可设置。大小 4k 左右
3.cookie 数据始终在同源的 http 请求中携带，在浏览器和服务器间来回传递。
读取 cookie

```js
function readCookie(name) {
  var nameEQ = name + "=";
  var ca = document.cookie.split(";");
  for (var i = 0; i < ca.length; i++) {
    var c = ca[i];
    while (c.charAt(0) == "") {
      c = c.substring(1, c.length);
      if (c.indexOf(nameEQ) == 0) {
        return c.substring(nameEQ.length, c.length);
      }
    }
    return null;
  }
}
```

#### 应用场景：

`sessionStorage`:

1.保存文本框输入的内容。浏览器偶然被刷新，文本框的内容也会会恢复(MDN 上的例子)。

```js
let field = document.getElementById("field");
if (sessionStorage.getItem("autosave")) {
  // 恢复文本内容
  field.value = sessionStorage.getItem("autosave");
}
// 监听文本输入框的change事件
field.addEventListener("change", function () {
  // 保存文本内容
  sessionStorage.setItem("autosave", field.value);
});
```

2. 记录列表中用户浏览的最后位置

通过监听 scroll 事件，`scrollTop()`获取位置。`sessionStorage`保存位置。
3.A 页面传递到 B 页面，即页面传值，按步骤引导用户填写的表单页面。

`localstorage`:

1.购物车信息。

2.页面的访问次数。
