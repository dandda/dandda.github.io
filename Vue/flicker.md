`Vue`实例数据渲染时出现闪烁的解决方法:

在挂载`el`元素上加上`v-cloak`

在 css 中也要加

```css
[v-cloak] {
  display: none;
}
```
