> 在我印象里能用到 onload 事件，就两个：一个 window,一个 img.当然还有其他的只是我几乎没用到过。
> onload 事件它是一个异步，这个要值得注意。
> onload 一般是一个 function(所以得将 this 用别的自定义变量，let that = this),无法用 es6 表示(()=>{})

#### window.onload

#### img.onload

在项目中遇到的运用场景。在 canvas 里

```javascript

draw_img(deviceName, ctx, x, y) {
  // 这里的图片在项目中换成请求后台接口返回的img地址即可。
        let imgSrc = 'http:xxxxxxxx.png'
        let img = new Image()
        //获取跨域图片，但是需要服务器端支持，请求返回头部要有：Access-Control-Allow-Origin:*。不然前端单独设置没用。
        img.crossOrigin = 'anonymous'
 img.src = imgSrc
        //图片加载完成，drawImage才能绘制到canvas
        img.onload = function() {
          // ctx.save()
          ctx.drawImage(this, x, y, 142, 160)
          // ctx.restore()
        }
      } else {
        ctx.clearRect(0, 0, ctx.width, ctx.height)
      }
    },
```
