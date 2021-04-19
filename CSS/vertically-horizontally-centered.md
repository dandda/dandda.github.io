#### 一.大小不固定，多行文字垂直居中

1. 单行文字，用`line-height`
2. 多行文字。
   父： `line-height`
   子：

   ```css
   display: inline-block;
   vetical-align: middle;
   line-height: normal <!--覆盖父元素的line-height, 即adjust. -->;
   ```

   3.模拟表格，图片也可
   父：

```css
display: table <!-- 没父元素，可以没这个 -->;
```

子:

```css
display: table-cell;
vetical-align: middle;
```

4. 绝对定位(父与子元素都必须有宽高)
   父：

```css
position: relative;
```

子:

```css
position: absolute;
top: 0;
right: 0;
bottom: 0;
let: 0;
margin: auto;
```

5. flexbox(弹性布局)
   一个元素：

```css
display: flex;
justify-content: center/flex-start/flex-end;
align-items: center;
```

两个元素：
父：display:flex;
子:margin:auto;

#### 二 图片垂直居中

1.background-position:center;
2.display:inline-block;vertical-align:middle;

3. 水平居中
   3.1 文字：text-align:center
   3.2 块级元素：margin:0 auto;
   3.3 不定宽块级元素，外层套个 table 标签，包括`<tbody>,<tr>,<td>`,给 table 设置 margin:0 auto;
   3.4 使块元素变为 inline 类型，再使用 text-align:center.
   3.5 给父元素设置：position:relative;left:50%;子元素设置：position:relative;left:-50%.
