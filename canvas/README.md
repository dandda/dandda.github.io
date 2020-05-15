## canvas 1px 的坑。

原理： 在 canvas 画的 1px 的线条在浏览器中有的是模糊，是因为 canvas 里的 1px 的线条有一条中线，一边 .5px,另一边.5px.如何下图，紫色部分为 1px![canvas_1px.png](https://i.loli.net/2020/04/26/pxHAdbtQW18T7VZ.png)

### 解决方法一:整体偏移 0.5px.这个只限水平或垂直的线。任何有倾斜角度的斜线无效。

```javascript
const ctx = document.getElementById(canvas).getContext("2d");
ctx.moveTo(0, 1 + 0.5);
ctx.lineTo(0, 2 + 0.5);
// or
ctx.translate(0, 0.5);
```

### 解决方法二：控制元素 canvas 的大小与绘制上下文的大小比率

canvas 有两个尺寸，一个是 css 尺寸，一个是画布的尺寸。所以这里又有两个方法来改变这个两个尺寸的比率。一个通过 css 改变，一个是通过 js 改变。

###### css 方法：

```html
<canvas id="canvas" width="600" height="300"></canvas>

<!-- css  画布的尺寸是css尺寸的两倍（可以多倍，按自己的想法来），这样就不会显的模糊了-->
<style>
  #canvas {
    width: 300px;
    height: 150px;
  }
</style>
```

###### js 方法：

```javascript
// 用这个方法的话，在<canvas></canvas>元素标签里就不需要设置width，height.但是css得设置width和height.
function setupCanvas(canvas) {
  // Get the device pixel ratio, falling back to 1.
  var dpr = window.devicePixelRatio || 1;
  // Get the size of the canvas in CSS pixels.
  var rect = canvas.getBoundingClientRect();
  // Give the canvas pixel dimensions of their CSS
  // size * the device pixel ratio.
  canvas.width = rect.width * dpr;
  canvas.height = rect.height * dpr;
  var ctx = canvas.getContext("2d");
  // Scale all drawing operations by the dpr, so you
  // don't have to worry about the difference.
  ctx.scale(dpr, dpr);
  return ctx;
}

// Now this line will be the same size on the page
// but will look sharper on high-DPI devices!
var ctx = setupCanvas(document.querySelector(".my-canvas"));
ctx.lineWidth = 5;
ctx.beginPath();
ctx.moveTo(100, 100);
ctx.lineTo(200, 200);
ctx.stroke();
```

[参考如下](https://www.html5rocks.com/en/tutorials/canvas/hidpi/)
