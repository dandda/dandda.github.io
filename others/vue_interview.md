#### js 是单线程还是多线程

单线程

#### 1.vue 是如何实现 mvvm 的,或者说对 mvvm 框架的理解？

MVVM 表示的是 Model-View-ViewModel
Model:模型层，负责处理业务逻辑和服务器端进行交互
View:视图层：负责将数据模型转化为 UI 展示出来
ViewModel:视图模型层，用来连接 Model 和 view,是 Model 和 View 之间的通信桥梁。
vue 框架起到的就是 ViewModel 层的作用。

#### 2.vue 与 react 的区别

#### 3 vue 有那几种导航钩子

三种，
一种是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
第二种：组件内的钩子；
第三种：单独路由独享组件

#### 4 vue 的生命周期，vue-router 的生命周期？

- vue 的生命周期：总共分为 8 个阶段创建前/后，载入前/后，更新前/后，销毁前/后。
  创建前/后： 在 beforeCreated 阶段，vue 实例的挂载元素$el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，$el 还没有。
  载入前/后：在 beforeMount 阶段，vue 实例的\$el 和 data 都初始化了，但还是挂载之前为虚拟的 dom 节点，data.message 还未替换。在 mounted 阶段，vue 实例挂载完成，data.message 成功渲染。
  更新前/后：当 data 变化时，会触发 beforeUpdate 和 updated 方法。
  销毁前/后：在执行 destroy 方法后，对 data 的改变不会再触发周期函数，说明此时 vue 实例已经解除了事件监听以及和 dom 的绑定，但是 dom 结构依然存在。

- route 的生存周期

```JavaScript
module.exports{
  data: function() {
    lifecycle.push("data");
    return {
      msg: "各个阶段，可以查看控制台输出，message from my-views",
      title: "my_views",
      lifecycle: lifecycle
    };
  },
  route: {
  //waitForData: true, // 数据加载完毕后再切换试图，也就是 点击之后先没反应，然后数据加载完，再出发过渡效果
  canActivate: function(transition) {
  // canActivate 阶段，可以做一些用户验证的事情(是否可以被激活)
  // 在验证阶段，当一个组件将要被切入的时候被调用。
  },
  activate: function(transition) {
  // 在激活阶段被调用，在 activate 被断定（ resolved ，指该函数返回的 promise 被 resolve ）。用于加载和设置当前组件的数据。(激活)
  //this.$root.$set('header',this.title);
  transition.next();
  //此方法结束后，api 会调用 afterActivate 方法
  //在 aftefActivate 中 会给组件添加 $loadingRouteData 属性 并设置为true
    },
  data: function(transition) {
    var _this = this;
    //  在激活阶段被调用，在 activate 被断定（ resolved ，指该函数返回的 promise 被 resolve ）。用于加载和设置当前组件的数据
    // 说明之前请求过 则不用再请求了
    if (this.$root.myViewsData) {
  this.$data = this.$root.myViewsData;
  transition.next();
  console.log("已经请求过了不再请求数据");
  return;
  }
    //将数据同步到根节点
    this.$root.myViewsData = this.$data;
    setTimeout(
      function() {
        //这里 _this.$loadingRouteData 是 true
        transition.next({ msg: "加载后的数据" });
        //在调用完transition.next 后，_this.$loadingRouteData 为 false
      }.bind(this),
      4000
    );
  },
  canDeactivate: function(transition) {
  // 在验证阶段，当一个组件将要被切出的时候被调用。(是否可以被禁用)
  },
  deactivate: function(transition) {
  // 在激活阶段，当一个组件将要被禁用和移除之时被调用。(禁用)
  }
  }
}
```

#### 5.vue 的双向数据绑定原理？

vue.js 是采用数据劫持结合发布者-订阅者模式的方式，vue2 通过 Object.defineProperty()来数据劫持，vue3 是通过 proxy.总结就是收集数据依赖，然后装到订阅器里，匹配 dom 中的指令，进行赋值。

#### 6.有三个页面（移动端，框架 vue），页面一是一个列表。列表中随机点击一个 item,进入到页面二，页面二是一个表单，表单有取消按钮和提交按钮，点击取消返回页面一，点击提交跳转到页面三。页面三显示的是提交成功的内容，有返回的按钮，返回到页面一。问：要这样实现时需注意的点及用户体验？

答：页面一需要注意的是，它是一个列表，自然会出现很多数数据，所以肯定需要一个 loading 加载页面。
页面一的数据应当存储在哪里，从页面一跳转到页面二，又从页面二跳回页面一，这里就会涉及到反复请求页面一的数据。面试官告诉我会把页面一的数据存到 vuex 里，数据没改变时无需请求数据。还有注意一个点就是在页面一往上滑动多条数据，跳到页面二，点击取消跳回页面一。页面一应当停留在之前离开的那条数据。页面二跳转到页面三应当用
`this.$router.repalce()`,减少路由跳转记录。页面三跳到页面一用`this.$router.go(-1)`即可，就不需要`go(-2),go(-3)`之类的了。

#### 7. 懒加载的原理

一种网页性能优化方式，img 的 src 会触发 http 请求，一开始不设置 src 值，当图片要出现时再设置 src 的值。现在`<img>`新增了一个`loading`的属性，其中一个值`lazy`可以实现延迟加载图片。就是兼容性不太好，有部分浏览器不支持。

#### 8.生成随机字符串（每次长度一样）

```js
// 方法一
function randomString(len) {
  // 字符串的长度
  len = len || 32;
  let t = "ABCDEFGHJKMNPQRSTWXYZabcdefhijkmnprstwxyz2345678",
    a = t.length,
    newString = "";
  for (let i = 0; i < len; i++) {
    // Math.random()表示从0-1之间的随机数(包括0，不包括1)。charAt()字符串方法，返回指定位置的字符
    newString += t.charAt(Math.floor(Math.random() * a));
  }
  return newString;
}
let re = randomString(8);
console.log("re", re);

// 方法二
// .toString(36) 转化成36进制
//.slice(-6);截取最后八位。
let str = Math.random().toString(36).slice(-6);
console.log("str", str);
```
