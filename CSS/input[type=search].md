> 在 iOS 移动端,修改 input 元素的默认样式时，即使设置了 border:0 也没用。得设置`-webkit-appearance:none`才有用。

修改 input[type=search]的默认样式

相关属性：

```html
<!-- result表示保存几条搜索记录 -->
<input type="search" result="5" />

<!-- x-webkit-speech 属性：在GOOGLE浏览器上 还会显示一个小话筒
autocomplete=”off” 属性 关闭浏览器自动记录之前输入的值 -->
```

```css
input[type="search"] {
  /* 让其变成一个普通的文字区域 */
  -webkit-appearance: textfield;
  -webkit-box-sizing: content-box;
  /* 其他样式自行设置，以覆盖默认样式 */
  outline: none;
}
/* input::-webkit-search-decoration的作用是填充‘❎’被移除后的所在空间位置。 */
input::-webkit-search-decoration,
input::-webkit-search-cancel-button {
  display: none;
}
input[type="search"]::-webkit-search-cancel-button {
  /* 自行设置（❎）叉号按钮样式 */
}
input[type="search"]::-webkit-search-cancel-button:after {
  /* 自行设置（❎）叉号按钮样式 */
}
/* 重写占位符，也就是提示语 */
input[type="search"]::-webkit-input-placeholder {
  color: lightblue;
}
input[type="search"]:focus {
  /* 当聚焦的时候使搜索框变大，一般这样的设计在移动端常见 */
}
```
