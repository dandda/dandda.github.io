> 提示 img 图片没有写 alt 属性或 alt 为空 的样式

```css
img:not([alt]),
img[alt=""] {
  border: 1px solid blue;
}
```

> 快速知道页面的布局

```css
* {
  border: 1px solid black;
}
```

> 给页面顶部加个阴影

```css
body::before {
  content: "";
  position: fixed;
  top: -10px;
  left: 0;
  width: 100%;
  height: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.8);
}
```

> a 标签没有链接填入 url

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```
