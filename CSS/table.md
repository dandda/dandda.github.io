实现 table 布局的方式有两种（以我现有的知识）。

> 直接给表格 tr 设置一个 border-bottom,是无效的。有以下方法解决：
>
> 1. 给 td 设置底部边框是可以的。
>    2.border-collapse:collapse,用来决定表格的边框是分开的还是合并的 ,再加 td { border-bottom: 1px solid #000; }

#### 1.table 标签

```html
<table>
  <!-- 表行 -->
  <tr>
    <!-- 表头 -->
    <th></th>
    <th></th>
    <th></th>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
```

#### 1.display:table

```html
<div class="list-table">
  <div class="list-row" v-for="(item,i) in classroom_list">
    <div class="list-cell">{{item.building}}</div>
    <div class="list-cell">{{item.floor}}</div>
    <div class="list-cell">{{item.classroom}}</div>
    <div class="list-cell onstatus" v-show="item.is_online">在线</div>
    <div class="list-cell offstatus" v-show="!item.is_online">离线</div>
  </div>
</div>
```

```css
.list-table {
  display: table;
}
.list-row {
  /* 表行 */
  display: table-row;
}
.list-cell {
  /* 类似td */
  display: table-cell;
}
```
