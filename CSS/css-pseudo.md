###### 分割线

**画分割线的第一种方法:使用`<hr>`和伪元素**

```css
.hr-text {
      position: relative;
      /* 注意这里要有足够的高度，文字才能正常显示 */
      height: 20px;
      text-align: center;
      /* 去除hr的边框 */
      border: none;
      opacity: 0.5;
    }
    .hr-text::before {
      content: "";
      position: absolute;
      left: 0;
      top: 50%;
      width: 100%;
      height: 1px;
      background-image: linear-gradient(
        to right,
        transparent,
        black,
        transparent
      );
    }
    .hr-text::after {
      content: attr(data-content);
      color: cadetblue;
      position: absolute;
      background-color: #fff;
      padding: 0 5px;
    }
<hr class="hr-text" data-content="AND">
<hr class="hr-text" data-content="OR">
```

---

**画分割线的第二种方法：伪元素和 flexbox**

```css
.p {
      display: flex;
      align-items: center;
      color: blue;
    }
    .p::before {
      content: "";
      height: 1px;
      flex-grow: 1;
      background-color: pink;
    }
    .p::after {
      content: "";
      flex-grow: 1;
      height: 1px;
      background-color: yellow;
    }

<p class='p'>我一条分割线</p>
```

[伪元素的不常见用例](https://ishadeed.com/article/unusual-use-cases-pseudo-elements/#header)
