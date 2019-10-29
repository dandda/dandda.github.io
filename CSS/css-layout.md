###### 1. 父元素两个子元素，一个子元素高固定，另一个子元素自适应剩下的高度

```html
<div class="contain">
  <header></header>
  <footer></footer>
</div>
```

```css
<!-- 法1 绝对定位和相对定位-->
.contain{
  position：relative
}
header{
  height:100px;
}
footer{
  position:absolute;
  top:100px;
  bottom:0;
}

<!--法2 比较推荐  flex弹性盒子 -->
.contain{
  display:flex;
  flex-direction:column;
}
header{
  height:100px;
}
footer{
  flex:1
}
```
