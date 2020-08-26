目前以我的知识开发要适配 pc 端和 mobile 端的方法
方法一：适用于比较简单的页面，pc 端和 mobile 端共用同一套页面，两套 css

方法二：页面复杂。pc 端和 mobile 端就要各自一套。
各自一套的话就需要有两个域名，一个域名用于 pc，另一个域名用于 mobile。既然有两个域名就得通过用户客服端的类型来判断，跳转到对应的域名。
代码如下：

```
if(navigator.userAgent.match(/iPad|iPhone|Android|BlackBerry|Windows Phone|webOS/i)){
    //this.$router.push({path:'/app'})
    // or window.location.href =''
}else{

}
```

假如有使用到@vue/cli 脚手架，还可以在 vue.config.js 配置多入口。
