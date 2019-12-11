##### 1.画有边框的三角形

```html
<!-- 向上的三角形 -->
<div class="triangle_border_up">
  <span></span>
</div>
<!-- 向左的三角形 -->
<div class="triangle_border_left"></div>
```

```css
.triangle_border_up {
  position: relative;
  width: 0;
  height: 0;
  /*  以上右下左边框属性来设置边框  */
  border-left: 100px solid transparent;
  border-right: 100px solid transparent;
  border-bottom: 100px solid black;
}
.triangle_border_up > span {
  position: absolute;
  left: -98px;
  top: -97px;
  width: 0;
  height: 0;
  /* 以 边框宽度、style、color属性，来设置边框 */
  border-width: 98px;
  border-style: solid;
  border-color: transparent transparent #fc0 transparent;
}
.triangle_border_left {
  position: relative;
  width: 0;
  height: 0;
  border-width: 100px 100px 100px 0;
  border-style: solid;
  border-color: transparent red transparent transparent;
}
.triangle_border_left::before {
  position: absolute;
  left: 1px;
  top: -98px;
  content: "";
  width: 0;
  height: 0;
  border-width: 98px 98px 98px 0;
  border-style: solid;
  border-color: transparent lightblue transparent transparent;
}
```

![triangle.png](https://i.loli.net/2019/12/11/uJzr9gXvOi784wm.png)

##### 2.气泡框

```html
<div class="triangle_border_wrap">
  <span>三角形</span>
  <div class="popup">纯CSS带边框的三角形</div>
</div>
```

```css
.triangle_border_wrap {
   position:relative;
  width:200px;
  text-align:center;
}
.popup {
  position:absolute;
  top:40px;
  width:200px;
  line-height:100px;
  height:100px;
  border:1px solid deeppink;
 background-color:lightblue;
  border-radius:4px;
}
.popup::before {
  position:absolute;
  left:50%;
  top:-20px;
  transform:translateX(-50%);
  content:'';
  width:0;
  height;0;
  border-width:0 20px  20px;
  border-style:solid;
  border-color:transparent transparent deeppink;
}
.popup::after {
  position:absolute;
  left:50%;
  top:-19px;
  transform:translateX(-50%);
  content:'';
  width:0;
  height;0;
  border-width:0 20px  20px;
  border-style:solid;
  border-color:transparent transparent lightblue;
}

```

![triangle1.png](https://i.loli.net/2019/12/11/I3rcnqfHXpEFjPV.png)

##### 3.西北、西南等朝向的三角形

```html
<div class="triangle_border_nw"></div>
```

```css
.triangle_border_nw {
  width: 0;
  height: 0;
  border-width: 30px 30px 0 0;
  border-style: solid;
  border-color: #6c6 transparent transparent transparent;
  margin: 40px auto;
  position: relative;
}
```

![triangle2.png](https://i.loli.net/2019/12/11/p5iuj21VtKmnUQf.png)

参考:[css 画三角形](https://www.cnblogs.com/blosaa/p/3823695.html)
