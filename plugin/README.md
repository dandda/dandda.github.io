#### 使用插件 html2canvas 的坑：

1.截取时如果页面过长出现滚动条，必须设置页面（这里设根元素）document.documentElement.scrollTop = 0 或者使之不能滚动的其他方法都可以。

2.被截的页面（组件），高和宽设 auto,就可以截取所有东西。否则只会截取到可见部分，不可见部分截不到。

3.很多时候截取的页面往往是很多内容拼接成的。然后这个页面生成的时候不能让用户看到。可以设置该页面为 margin: -999999px;

> 注意 打印 PDF 不一定要使用插件，可以使用 js 自带的 window.print()

#### elementui

elementui 的 el-dialog 弹框被遮罩层盖住（我这里用了 v-for）,循环多个一样的弹框就会出现这种情况。这里就是循环的多个弹框一样没有给唯一标识才导致的问题

# xlsx-style

> 前端导出 excel 表格的一个插件，可以设置表格单元格的宽度等样式。（挺久远的一个，早已经不更新了。）,不知道还有什么插件可以替换。
> 安装报错。在报错的地方如下修改就可以了
> var cpt = require(’./cpt’ + ‘able’); 改成 var cpt = cptable;

#js-xlsx

> 前端导出 excel 表格的一个插件。免费版不提供表格的样式修改。所以才使用了上面 `xlsx-style`插件代替。

```
aoa_to_sheet //将二维数组转成sheet
json_to_sheet //由对象转成sheet
table_to_sheet //将一个table dom 直接转成sheet

```
