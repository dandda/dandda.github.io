> 在 iOS 移动端,修改 input 元素的默认样式时，即使设置了 border:0 也没用。得设置`-webkit-appearance:none`才有用。

##### 修改 input[type=search]的默认样式

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

---

##### 修改单选按钮[type='checkbox']的 input 默认样式

###### 两种结构

1.对原有样式改变不是很大

```html
<input type="checkbox" id="test" class="example1" />
<!-- label通过for属性指向input,当操作label时input才会有 -->
<label for="test"><span></span>checkbox1 </label>
```

```css
.example1 {
  display: none;
}
.example1 + label {
}
.example1 + label > span {
  /* 自行设置想要的样式 */
  background: url() center no-repeat;
}
.example1: checked + label>span {
  /* 选中的样式 */
}
```

![checkbox.png](https://i.loli.net/2019/12/11/nQpIUztAJCvmBPZ.png)

2.

```html
<input class="switch switch-anim" type="checkbox" checked />
```

```css
.switch {
  width: 57px;
  height: 28px;
  position: relative;
  border: 1px solid #dfdfdf;
  background-color: #fdfdfd;
  box-shadow: #dfdfdf 0 0 0 0 inset;
  border-radius: 20px;
  background-clip: content-box;
  display: inline-block;
  /* 移除原生控件样式 */
  -webkit-appearance: none;
  user-select: none;
  outline: none;
}
.switch:before {
  content: "";
  width: 26px;
  height: 26px;
  position: absolute;
  top: 0;
  left: 0;
  border-radius: 20px;
  background-color: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
}
.switch:checked {
  border-color: #64bd63;
  box-shadow: #64bd63 0 0 0 16px inset;
  background-color: #64bd63;
}
.switch:checked:before {
  left: 30px;
}
.switch.switch-anim {
  transition: border cubic-bezier(0, 0, 0, 1) 0.4s, box-shadow cubic-bezier(
        0,
        0,
        0,
        1
      ) 0.4s;
}
.switch.switch-anim:before {
  transition: left 0.3s;
}
.switch.switch-anim:checked {
  box-shadow: #64bd63 0 0 0 16px inset;
  background-color: #64bd63;
  transition: border ease 0.4s, box-shadow ease 0.4s, background-color ease 1.2s;
}
.switch.switch-anim:checked:before {
  transition: left 0.3s;
}
```

![checkbox2.png](https://i.loli.net/2019/12/10/pxOZLoMI38gzCQj.png)

##### 修改原生下拉框 select 的 input 默认样式

```css
/* 修改默认样式 */
select {
  border: none;
  background-color: transparent;
  appearance: none;
  -moz-appearance: none;
  -webkit-appearance: none;
  outline: none;
}

/* 要让select 文字居中(option就不知道了) 光写text-align:center无效 */
select {
  /* 这两个属性都设为center,select文字就可以居中。注意不能设置具体width数值。 */
  text-align: center;
  text-align-last: center;
  /* 宽度为auto,上面两个属性才有效 */
  width: auto;
}
```

> 如果以上都不能满足，那就只能将 select 隐藏，使用 label 指向 select 自己写。
