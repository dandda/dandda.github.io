vue

- [v-on](#v-on)

#### v-on

> 通常我都会一个`v-on`（缩写@）绑定一个方法，当面试突然问到是否可以绑定多个方法时，我迟疑了并回答了好像可以，
> 然后去浏览器搜了下，确实可以。因为我在项目中@click 一般只绑定一个方法，从来没有绑定多个方法。所以我才不确定。以此记录下。`v-on:click`缩写为`@click`,`v-on:mouseenter`缩写为`@mouseenter`

例子：

```html
<button v-on="{mouseenter: onEnter,mouseleave: onLeave}">
  鼠标移进，移除1
</button>
<button @mouseenter="onEnter" @mouseleave="onLeave">鼠标移进，移除2</button>
<button @click="a(),b()">点我ab</button>
```

```javascript
  a(){
      console.log('a');
    },
  b(){
      console.log('b');
    },
   onEnter(){console.log("mouseenter");},
   onLeave(){console.log("mouseleave");}

  }
```
