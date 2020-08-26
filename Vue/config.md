> 主要讲脚手架 vue-cli 3.0 的配置。vue-cli 3.0 改名称为`@vue/cli`。以下皆以`@vue/cli`为主语。
> @vue-cli 版本以前的配置，都把基本配置配好了。然后在`@vue/cli`需要自己手动配置了。

#### 1.环境配置

在项目根下新建.env 文件，所有环境下都使用的是.env 里的 api。

如果不同环境要调用不同的接口。则新建对应的.env 文件。
开发环境：新建`.env.development`文件。文件内容如下

VUE_APP_BASE_API=http://www.tecxen.com

> 当 VUE_APP_BASE_API = 时即不填，则 api 表示为空，就等于用户用哪个域名访问，接口地址就是那个域名。注意 api 有端口号的不能这样。

测试环境： 新建`.env.test`文件。内容如上一样 api 改成测试的 api 即可

生产环境： 新建`.env.production`文件。内容同理。

在 package.json 里的 script 加入 test

```javascript
"scripts": {
    "serve": "vue-cli-service serve", //启动项目
    "build": "vue-cli-service build",  //打包，打包之后api是.env.production文件里设置的API
    "test": "vue-cli-service build --mode test", //打包为测试环境api的包，终端输入的命令为 npm run test
    "lint": "vue-cli-service lint"
  }
```

2.  根目录新建 `vue.config.js`文件

- 这里只配置压缩并去掉 console,还可以配置其他好多东西（查看文档）

```javascript
//压缩代码并去掉console
const UglifyJsPlugin = require("uglifyjs-webpack-plugin");
module.exports = {
  lintOnSave: false,
  assetsDir: "static",
  transpileDependencies: ["vue-baidu-map"], //这个是百度地图的插件。需要处理es6为es5（babel不会处理node_modules里的东西）.不然打包时会报错,假如还使用了其他类似的插件，都需要在这里添加一下。
  configureWebpack: config => {
    if (process.env.NODE_ENV === "production") {
      // 生产环境
      const plugins = [];
      //启用代码压缩
      plugins.push(
        new UglifyJsPlugin({
          uglifyOptions: {
            compress: {
              drop_console: true,
              // drop_debugger: false,
              pure_funcs: ["console.log"] //移除console
            }
          },
          sourceMap: false,
          parallel: true
        })
      );

      config.plugins = [...config.plugins, ...plugins];
    } else {
      // 开发环境
    }
  }
};
```

- 别名配置 百度来的，有待检验

```javascript
const path = require("path");
function resolve(dir) {
  return path.join(___dirname, dir);
}
module.exports = {
  chainWebpack: config => {
    config.resolve.alias
      .set("@", resolve("src"))
      .set("style", resolve("src/asset/style"));

    // filenameHashing:false
    // true则将静态资源文件名转为带有哈希值的名字。
  }
};
```
