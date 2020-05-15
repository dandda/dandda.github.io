##### 浏览器访问优化

![browser_request_process.png](https://i.loli.net/2019/12/20/v3Om16ZdGFD9c7R.png)

> 1. 减少 http 请求，合理设置 http 缓存

    减少 http 的主要手段是合并 CSS、合并 javascript、合并图片。例如很少变化的图片资源可以直接通过 HTTP Header 中的 Expires 设置一个很长的过期头 ;变化不频繁而又可能会变的资源可以使用 Last-Modifed 来做请求验证。

> 2. 浏览器缓存（搞不懂与 http 缓存有什么区别）

    通过设置 http 头中的 cache-control 和 expires 的属性，可设定浏览器缓存，缓存时间可以是数天，甚至是几个月。

> 3. CSS Sprites

    合并css图片，减少请求数

> 4. 懒加载

> 5. css 放在页面最上面，javascript 放在下面

> 6. 异步请求 callback

##### javascript 代码优化

> 1. 减少对 DOM 的操作。

    获取dom元素的时候，例如`document.getElementsById()`, `documents.forms`.返回的都是一个`HTML collection`的集合，
    遍历这些的集合的时候转化为数组，再访问可以提高性能。直接访问会每次重新查询。
    转化为数组相当于用一个变量暂存了，访问就不会在重新查询了。

> 2. 减少作用域链查找

```javascript
let globalNum = 1;
function my() {
  for(let i =100;i--){
    //每次访问 globalVar 都需要查找到作用域链最顶端，本例中需要访问 100 次
    globalNum += i

  }
}
```

```javascript
let globalNum = 1;
function my() {
  // 局部变量缓存全局变量
  let localNum = globalNum;
  for (let i = 100; i--; ) {
    // 访问局部变量是最快的
    localNum += i;
  }
  // 这里只需要访问两次globalNum.
  globalNum = localNum;
}
```

> 数据访问

    Javascript中的数据访问包括直接量 (字符串、正则表达式 )、变量、对象属性以及数组，其中对直接量和局部变量的访问是最快的，
    对对象属性以及数组的访问需要更大的开销。当出现以下情况时，建议将数据放入局部变量：
        a. 对任何对象属性的访问超过 1 次
        b. 对任何数组成员的访问次数超过 1 次
        另外，还应当尽可能的减少对对象以及数组深度查找。

> css 选择符优化

    浏览器对css选择符的解析是从右到左的。

> cdn

> 反向代理

参考：

1. [web 性能优化](https://xuetengfei.github.io/#/Progress/web-performance-optimization)
2. [web 性能优化](https://blog.csdn.net/mahoking/article/details/51472697)
3. [web 性能讨论](https://github.com/barretlee/performance-column/issues)
