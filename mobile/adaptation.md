我都是用于移动端的 reset.js,单位用的是 rem.

```javascript
function resetFontSize() {
  var windowW = document.documentElement.clientWidth;
  var scale = windowW / 375;
  var newSize = 100 * scale;
  document.getElementsByTagName("html")[0].style.fontSize = newSize + "px";
}
window.addEventListener("resize", resetFontSize, false);
resetFontSize();
```

貌似这个 rem 适配已经不大使用了。手机淘宝团队已经有一套 flexible.js 来代替。
