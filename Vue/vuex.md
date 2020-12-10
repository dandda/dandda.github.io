vue 并不限制你的代码结构，但规定了要遵守的规则

1. 应用级的状态应该集中到单个 store 对象中
2. 提交 mutation 是更改状态的唯一方法。并且是同步的
3. 异步逻辑都应该封装到 action 里

在组件中 使用 `this.$store.dispatch('addCart',data)`
在 actions 里 addCart({commit},data){

<!-- 这里进行一些请求 -->

commit（'ADD_CART',data）

}
在 mutations:{
ADD_CART(){

<!-- 更新state及页面 -->

}

}
