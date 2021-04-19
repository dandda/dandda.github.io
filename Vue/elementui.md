element-ui 表格的表头循环
js 文件

```js
import { formateTime } from "../../../util";
export const deviceLogColumn = [
  {
    tableProp: "devNo",
    tableLabel: "设备编号",
  },
  {
    tableProp: "logName",
    tableLabel: "文件名",
  },
  {
    tableProp: "addDate",
    tableLabel: "创建时间",
  },
];
export const formatData = (arr) => {
  return arr.map((v) => ({
    ...v,
    addDate: formateTime(v.addDate),
  }));
};
```

vue 文件:

```html
<el-table :data="deviveLogData" border style="width: 100%">
  <el-table-column
    v-for="v in table"
    :prop="v.tableProp"
    :key="v.tableProp"
    :label="v.tableLabel"
  ></el-table-column>
  <el-table-column label="操作" width="150">
    <template slot-scope="scope">
      <a style="color:#409EFF" :href="scope.row.logUrl">下载</a>
    </template>
  </el-table-column>
</el-table>
<!-- deviveLogData为原始数据，没被修改过-->
```

```js
import { deviceLogColumn, formatData } from "./own/deviceLog.js";
mounted() {
    this.table = deviceLogColumn

  }
```
