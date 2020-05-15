##### 1.数组对象里有某个属性值一样的进行统计，累计数量。

举例

```javascript
let device_arr = [
  {
    id: 1421,
    pid: 14,
    equipmentName: "节点控制单元（显示）",
    equipmentNicname: "一体机",
    num: 3,
    prid: 83
  },
  {
    id: 1422,
    pid: 14,
    equipmentName: "节点控制单元（显示）",
    equipmentNicname: "投影机",
    num: 2,
    prid: 84
  },
  {
    id: 1423,
    pid: 14,
    equipmentName: "节点控制单元（幕布）",
    equipmentNicname: "幕布",
    num: 4,
    prid: 85
  },
  {
    id: 1424,
    pid: 14,
    equipmentName: "节点控制单元（扩声）",
    equipmentNicname: "功放",
    num: 4,
    prid: 86
  },
  {
    id: 1425,
    pid: 14,
    equipmentName: "节点控制单元（电脑）",
    equipmentNicname: "电脑",
    num: 2,
    prid: 87
  }
];
// 如上数据，一体机和投影机对应的都是同一个产品节点控制单元(显示)。让这两条数据只显示一条并且这两条数据里num相加。
let new_device_arr = [];
device_arr.map((d, i) => {
  let result = new_device_arr.findIndex(n => {
    return d.equipmentName === n.equipmentName;
  });
  if (result !== -1) {
    new_device_arr[result].num = new_device_arr[result].num + d.num;
  } else {
    new_device_arr.push(d);
  }
});
console.log("new_deviec_arr", new_device_arr);
// [{id: 1421, pid: 14, equipmentName: "节点控制单元（显示）", equipmentNicname: "一体机", num: 5, prid: 83}, {id: 1423, pid: 14, equipmentName: "节点控制单元（幕布）", equipmentNicname: "幕布", num: 4, prid: 85},{id: 1424, pid: 14, equipmentName: "节点控制单元（扩声）", equipmentNicname: "功放", num: 4,  prid: 86}, {id: 1425, pid: 14, equipmentName: "节点控制单元（电脑）", equipmentNicname: "电脑", num: 2,  prid: 87}]
```

##### 2.如下述数据结构，要求判断任意一个电源组 status 里的所有 is_enable 都为 true 则 true，只要有一个 false 则为 false。

```javascript
const all_powers = [
  {
    status: [
      { status: true, is_enable: true, name: "1路电源" },
      { status: true, is_enable: true, name: "2路电源" },
      { status: true, is_enable: true, name: "3路电源" },
      { status: true, is_enable: true, name: "4路电源" }
    ],
    counts: 0,
    id: 46,
    time: "2020-03-03 10:35:47",
    name: "总电源1"
  },
  {
    status: [
      { status: true, is_enable: true, name: "1路电源" },
      { status: true, is_enable: false, name: "2路电源" },
      { status: true, is_enable: true, name: "3路电源" },
      { status: true, is_enable: true, name: "4路电源" }
    ],
    counts: 0,
    id: 46,
    time: "2020-03-03 10:35:47",
    name: "总电源2"
  }
];

// 方法一 多加了一个属性totalStatus，用来判断用
for (let i = 0; i < all_powers.length; i++) {
  let statusArr = [];
  for (let status of all_powers[i].status) {
    statusArr.push(status.is_enable);
  }
  if (statusArr.includes(false)) {
    all_powers[i].totalStatus = false;
  } else {
    all_powers[i].totalStatus = true;
  }
  console.log("all_powers", all_powers);
}

// 方法二
let result;
all_powers.map(i => {
  result = i.status.findIndex(ii => {
    return ii.is_enable === false;
  });
  if (result !== -1) {
    i.totalStatus = false;
  } else {
    i.totalStatus = true;
  }
});
```
