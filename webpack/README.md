###### 第一问：项目打包后文件依然很大，要如何解决

1.使用 cdn,某些依赖可以用 cdn

2.进行压缩

3.对安装的依赖进行分包，配置如下

```js
// vue3.0的vue.config.js里的配置
config.optimization.splitChunks({
  chunks: "all",
  cacheGroups: {
    libs: {
      name: "chunk-libs",
      test: /[\\/]node_modules[\\/]/,
      priority: 10,
      chunks: "initial", // only package third parties that are initially dependent
    },
    elementUI: {
      name: "chunk-elementUI", // split elementUI into a single package
      priority: 20, // the weight needs to be larger than libs and app or it will be packaged into libs or app
      test: /[\\/]node_modules[\\/]_?element-ui(.*)/, // in order to adapt to cnpm
    },
    commons: {
      name: "chunk-commons",
      test: resolve("src/components"), // can customize your rules
      minChunks: 3, //  minimum common number
      priority: 5,
      reuseExistingChunk: true,
    },
  },
});
```
