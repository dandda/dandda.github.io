#### vue-cli 引入图片的方式

1. 图片放在 static 目录下,直接使用图片的绝对路径（config/index.js 设置）。在 static 下的图片不会经过 webpack 打包编译。

   - 直接在 img 的 src 上填入路径

   ```javascript
     //template
     <template>
      <div>
        <img src="../../../static/img/logo.png" alt="898989">
      </div>
     </template>
      //在浏览器的调试查看里图片路径不知道为什么会变成base64超长的名字
      //在style里也是直接使用图片的绝对路径,也是可以的
      <style>
      img{
        background-image:url('../../../static/img/logo.png')
      }
      </style>

   ```

2. 图片在 assets 目录下的三种引入方式

   2.1 也是直接在 img 的 src 写入路径(相对路径)

   ```javascript
   <template>
    <div>
       <img src= '../assets/logo.png'>
    </div>
   </template>

   ```

   2.2 通过 import 引入

   ```javascript
    //template
    <template>
      <div id='app'>
         <img :src='imgUrl'>
      </div>
    </template>

    //script
    import imgUrl form '../assets/logo.png'
    export default {
      data () {
        return {
          imgUrl:imgUrl
        }
      }
    }
   ```

   2.3 通过 require

   ```javascript
     <template>
       <div id="app">
         <img :src="require('./assets/logo.png')" />
       </div>
     </template>
   ```

   2.4 还有一种情况是在 css 的 background-image 里引入图片

   ```javascript
     <style>
       img {
         // 前缀'~'视为模块请求，对webpack来说
         background-image:url('~assets/logo.png');
         // 或者
         // background-image:url(require('./assets/logo.png'));
       }
     </style>
   ```

#### 通过阿里 iconfont 引入图标库

在 vue(vue-cli2.0) 将阿里 iconfont 的项目里用 symbol 的方式引入(已经是将图标下载到本地的)，在 index.html 使用 script 标签导入会报错。在 main.js 里使用 import 引入就没问题了
