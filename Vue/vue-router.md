第一种导出方法
在 router/index.js

```import Router from "vue-router";
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

```import router from "./router";
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
