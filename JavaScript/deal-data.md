##### 1.数组对象里有某个属性值一样的进行统计，累计数量。

举例

```javascript
let device_arr = [
  {
    id: 1,
    equipmentName: "设备类别1",
    equipmentNicname: "一体机",
    num: 3,
  },
  {
    id: 2,
    equipmentName: "设备类别1",
    equipmentNicname: "投影机",
    num: 2,
  },
  {
    id: 3,
    equipmentName: "设备类别2",
    equipmentNicname: "幕布",
    num: 4,
  },
  {
    id: 4,
    equipmentName: "设备类别3",
    equipmentNicname: "灯光",
    num: 4,
  },
  {
    id: 5,
    equipmentName: "设备类别4",
    equipmentNicname: "电脑",
    num: 2,
  },
];
// 如上数据，一体机和投影机对应的都是同一个设备类别。让这两条数据只显示一条并且这两条数据里num相加。
let new_device_arr = [];
device_arr.map((d, i) => {
  let result = new_device_arr.findIndex((n) => {
    return d.equipmentName === n.equipmentName;
  });
  if (result !== -1) {
    new_device_arr[result].num = new_device_arr[result].num + d.num;
  } else {
    new_device_arr.push(d);
  }
});
console.log("new_deviec_arr", new_device_arr);
// [{id: 1,  equipmentName: "设备类别1", equipmentNicname: "一体机", num: 5}, {id: 2, equipmentName: "设备类别2", equipmentNicname: "幕布", num: 4},{id: 3,  equipmentName: "设备类别3", equipmentNicname: "灯光", num: 4}, {id: 4,  equipmentName: "设备类别4", equipmentNicname: "电脑", num: 2}]
```

##### 2.如下述数据结构，要求判断任意一个总路组 status 里的所有 is_enable 都为 true 则 true，只要有一个 false 则为 false。

```javascript
const roads = [
  {
    status: [
      { status: true, is_enable: true, name: "支路1" },
      { status: true, is_enable: true, name: "支路2" },
      { status: true, is_enable: true, name: "支路3" },
      { status: true, is_enable: true, name: "支路4" },
    ],
    counts: 0,
    id: 1,
    name: "总路1",
  },
  {
    status: [
      { status: true, is_enable: true, name: "支路1" },
      { status: true, is_enable: false, name: "支路2" },
      { status: true, is_enable: true, name: "支路3" },
      { status: true, is_enable: true, name: "支路4" },
    ],
    counts: 0,
    id: 1,
    name: "总路2",
  },
];

// 方法一 多加了一个属性totalStatus，用来判断用
for (let i = 0; i < roads.length; i++) {
  let statusArr = [];
  for (let status of roads[i].status) {
    statusArr.push(status.is_enable);
  }
  if (statusArr.includes(false)) {
    roads[i].totalStatus = false;
  } else {
    roads[i].totalStatus = true;
  }
  console.log("roads", roads);
}

// 方法二
let result;
roads.map((i) => {
  result = i.status.findIndex((ii) => {
    return ii.is_enable === false;
  });
  if (result !== -1) {
    i.totalStatus = false;
  } else {
    i.totalStatus = true;
  }
});
```
