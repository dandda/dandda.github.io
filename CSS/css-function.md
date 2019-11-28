##### 1. var() 插入自定义属性的值

定义一个属性名，使用`var()`函数将该属性名的值放入到样式中。

定义的属性名的以两个横杠开头，写在`:root{}`里。

```html
<style>
  :root {
    --bg: yellow;
    --text-color: rgba(1, 14, 15, 0.7);
  }
  .test {
    background-color: var(--bg);
    color: var(--text-color);
  }
</style>
<body>
  <div class="test">w我黄了我黄了</div>
</body>
```

##### 2. calc() 计算属性值

通常来计算元素的宽度和高度，在要求自适应的页面可以使用。

```html
<style>
  .site {
    height: 100%;
  }
  .site-head {
    height: 100px;
  }
  /* 自动填充剩余空间,注意 ‘-，+’等运算符前后都要留有一个空格 */
  .site-content {
    height: calc(100% - 100px);
  }
</style>
<body>
  <div class="site">
    <div class="site-head"></div>
    <div class="site-content"></div>
  </div>
</body>
```

##### 3. linear-gradient(direction, color-stop1, color-stop2, ...)

设置线性渐变作为背景图像。

> 刚好前几天遇到有关渐变的问题：在 vue 里有个变量，这个变量的样式为文字渐变。当这个变量的值改变时，按理说界面应该显示最新的值才对,但是>它没有。把`linear-gradient()`的样式去掉。就不会有问题.至于渐变为什么会引发渲染的问题，我也不清楚。

如果非要用渐变不可的话，有以下三种方法解决：

**(1). v-text**

**(2). mask 属性**

**(3). 将类名.time1 的 display 设置为 unset 或者 inline**

```html
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Demo</title>
    <style>
      body {
        font-size: 40px;
      }
      .time1 {
        display: inline-block;
        background: linear-gradient(to right, #a6ffcb, #1fa2ff);
        -webkit-background-clip: text;
        color: transparent;
      }
      /*方法三  */
      .time3 {
        display: inline;
        /* display:unset */
        background: linear-gradient(to right, #a6ffcb, #1fa2ff);
        -webkit-background-clip: text;
        color: transparent;
      }
      /* ------------ */
      /* 方法二 */
      .time2 {
        position: relative;
        color: #a6ffcb;
      }
      .time2::before {
        color: #1fa2ff;
        content: attr(t);
        position: absolute;
        -webkit-mask: linear-gradient(to right, transparent, #1fa2ff);
      }
    </style>
  </head>
  <body>
    <div id="app">
      <!-- 不正常 -->
      <div class="time1">{{ time }}</div>
      <!-- 正常 -->
      <div>{{time}}</div>

      <!-- 解决方法一 -->
      <div class="time1" v-text="time"></div>
      <!-- 解决方法二 -->
      <div class="time2" :t="time">{{time}}</div>
      <!-- 解决方法三 -->
      <div class="time3">{{ time }}</div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.min.js"></script>
    <script>
      new Vue({
        el: "#app",
        data: {
          time: new Date().toLocaleString()
        },
        methods: {
          updateTime() {
            this.time = new Date().toLocaleString();
          }
        },
        mounted() {
          setInterval(this.updateTime, 1000);
        }
      });
    </script>
  </body>
</html>
```

参考如下：
[vue 中使用文字渐变引发的渲染问题](https://juejin.im/post/5dca0b62e51d4559466e2ff1?utm_medium=hao.caibaojian.com&utm_source=hao.caibaojian.com)
