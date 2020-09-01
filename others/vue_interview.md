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
