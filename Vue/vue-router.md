- [导出方法](#导出方法)
- [路由传参的区别（query,params）](#路由传参的区别)
- [路由模式 history 和 hash 的区别](#路由模式)
- [$route与$router 的区别](#$route与$router的区别)

### 导出方法

第一种导出方法
在 router/index.js

```
import Router from "vue-router";
Vue.use(Router);
const router = new Router({
  routes:[{
    path:'/login',
    component: () => import("../views/login")
  }],
  ...
})
```

在 `.main.js`中引入

```
import router from "./router";
new Vue({
el: "#app",
router,
template: "<App/>",
components: { App }
});
```

第二种导出方法
在`router/index.js`中

```
import Router from "vue-router";
Vue.use(Router);
export function createRouter() {
  return new Router({
    routes: [
      {
        path: "/login",
        component: () => import("../views/login")
      }
    ]
  });
}
```

在`main.js`中引入

```
import { createRouter } from "./router"
new Vue({
  router: createRouter(),
  render: h => h(App)
}).$mount("#app");
```

----------------------------要多看 vue-router 文档呀--------------------------

##### vue-router 中进入首页，然后首页里有一个二级路由。一般进入首页都会要默认显示这个二级路由。有两种方法：

#### 1.第一个是子路由不设置 path,path 为空

```javascript
{
    path: "/",
    name: "Home",
    component: () => import("../views/home/index.vue"),
    children: [
    //子路由
      {
        path: "",
        component: () => import("../views/home/showCase/index.vue")
      }
    ]
  }
```

#### 2.第二个就是用 redirect

```javascript
{
    path: "/",
    name: "Home",
    component: () => import("../views/home/index.vue"),
    redirect:'/case'
    children: [
      {
        path: "/case",
        component: () => import("../views/home/showCase/index.vue")
      }
    ]
}
```

### 路由传参的区别

> query 通过 path 传地址`this.$router.push({path:"地址",query:{id:"123"}})`，接受参数： >`this.$route.query.id`;在页面刷新时不会丢失参数；传的参数显示在地址栏中。

> params 通过`name`传地址`this.router.push({name:'地址',params:{id:'123}})`,接受参数：`this.$route.params.id`;页面刷新会丢失参数；不会显示参数在地址栏
> params 刷新丢失参数的处理方法：1.路由设置把参数拼 url 上，也就是使他转换成 query 的方式。2.sessionstorage 存储。

### 路由模式

> vue-router 默认 hash 模式

> hash：1.url 里会有‘#’，url 改变时页面不会重新加载。 2. 通过 window.onhashchange 监听 hash 的变化，来操作路由。3.缺点：改变 url 时不算一次 http 请求，因此不利于 seo 优化。

> history: 1.重新刷新页面时，如果后台没有做相应的配置，会出现 404。所以要在服务器端增加一个覆盖所有情况的候选资源：如果 url 匹配不到任何静态资源，则应该返回同一个 index 页面。 2.通过 history 的 API，history.pushState()和 history.replaceState()实现无刷新跳转。 3. 新的 URL 可以是与当前 URL 同源的任意 URL，也可以与当前 URL 一样，但是这样会把重复的一次操作记录到栈中

### $route与$router 的区别

1.router 为 VueRouter 实例，想要导航到不同 URL，则使用 router.push 方法
2.$route 为当前 router 跳转对象(当前激活的路由的信息对象)，里面可以获取 name、path、query、params 等
