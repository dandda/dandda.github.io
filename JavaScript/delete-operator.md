用于删除某个-对象-的某个属性

- 删除不存在的属性，也会返回`true`。
- 如果对象的原型链上有一个与待删除的属性同名的属性，delete 只会删除自身的属性，不会删除原型链的。
- 任何用`let`或`const`声明的属性不能够从它被声明的作用域中删除。
- 任何使用 var 声明的属性不能从全局作用域或函数的作用域中删除。

  - 这样的话，delete 操作不能删除任何在全局作用域中的函数（无论这个函数是来自于函数声明或函数表达式）

  - 除了在全局作用域中的函数不能被删除，在对象(object)中的函数是能够用 delete 操作删除的。

- 不可设置的属性不可移除

```javascript
const person = [
  {
    name: "jack",
    sex: "male",
    nation: "han",
    visible: "false"
  },
  {
    name: "rose",
    sex: "female",
    nation: "han",
    visible: "false"
  }
];
delete person[0].name; //返回 true
```

<h4>我遇到使用过的`delete`的场景</h4>

**1. 批量删除不需要的属性**

比如不想要`person`里面的`visible`属性，example:

```javascript
for (let item of person) {
  delete item.visible;
}
console.log(person);
//  [{
//     name: "jack",
//     sex: "male",
//     nation: "han"
//   },
//   {
//     name: "rose",
//     sex: "female",
//     nation: "han"
//   }]
```

**2. 比如编辑设备详情时，多组设备时（v-for 循环出来）。你可以点击任意一组展开和收起被点击的那组详情，控制展开和收起需要一个 bool 值，因为是循环出来的你无法用一个变量去控制对应的组，然而后台数据没有给你的话，这时你可以自己添加一个属性进去，比如我添加一个`visible`属性进去去控制展开和收起。记住别忘了，因为是你自己添加的，传给后台时得删除`visible`这个属性**
