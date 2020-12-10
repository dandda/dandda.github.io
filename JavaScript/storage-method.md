#### localStorage and sessionStorage

相对新的 API，api 和功能基本相同。

区别在于持久性：sessionStorage（仅在浏览器会话窗口里可用，关闭浏览器窗口或选项卡就会移除）,但是重新加载页面还是可以保留的。
都非常适合在页面之间的客户端脚本中持久存储所需的非敏感数据。

cookie:通常，cookie 用于存储身份验证，会话和广告跟踪的标识令牌。

应用场景：

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
