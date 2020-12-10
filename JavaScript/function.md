#### 匿名函数

没有函数名的参数

```javascript
//这里定义匿名函数，直接这样写会语法错误。因为如果可以这样定义的话，这个函数根本无法调用。把它赋值给一个变量就不会有问题了
//function () {}

//声明了一个匿名函数，并把匿名函数赋值给变量f
let f = function () {};
//把f当成一个函数名
f(); // 调用上面定义的匿名函数
```

#### 匿名函数的作用

**1.匿名函数可以作为一个参数传递给其他函数**

**2.通过一个匿名函数完成一个一次性的任务，如果一个函数不需要重复执行，就可以使用匿名函数**

#### 匿名函数立即执行

```javascript
(function () {})();
```

> 说明

1.把匿名函数用一对括号括起来，当成一个整体。

2.最后在添加一对括号，表示函数调用，就会立即执行。

#### 函数的递归调用

> 在函数的内部调用当前函数，自己调用自己。

> 递归要满足以下两个条件，不然会出现死循环:
>
> 1.  一定要有结束条件。
>
> 2.  随着函数的递归深入，要不断接近结束条件。

> **例子 1: 阶乘**,对递归不够了解。还要多看看和练习。

```javascript
function jiecheng(num) {
  if (num === 0) {
    return 1;
  }
  jiecheng(num - 1) * num;
}
jiecheng(4); //24
```

> **例子 2:多叉树**

![多叉树.jpg](https://i.loli.net/2019/12/11/41pWURtI5ixqQsF.jpg)

```javascript
let handleData = {
  name: "全校",
  id: 1,
  children: [
    {
      name: "楼宇1",
      id: 11,
      children: [
        {
          name: "楼宇1-楼层1",
          id: 111,
          children: [
            {
              name: "楼宇1-楼层1-教室1",
              id: 1111,
            },
            {
              name: "楼宇1-楼层1-教室2",
              id: 1112,
            },
          ],
        },
        {
          name: "楼宇1-楼层2",
          id: 112,
          children: [
            {
              name: "楼宇1-楼层2-教室1",
              id: 1211,
            },
          ],
        },
      ],
    },
    {
      name: "楼宇2",
      id: 12,
      children: [
        {
          name: "楼宇2-楼层1",
          id: 121,
        },
      ],
    },
  ],
};

// 获取节点的所有叶子节点的个数
function getLeafCountTree(data) {
  if (!data.children) {
    return 1;
  } else {
    let leafCount = 0;
    for (let i = 0; i < data.children.length; i++) {
      leafCount += getLeafCountTree(data.children[i]);
    }
    return leafCount;
  }
}
console.log(getLeafCountTree(handleData)); //4
```

#### arguments 对象

> 在调用函数的时候，会自动创建一个 arguments 对象。是所有（非箭头）函数中都可用的局部变量。
> arguments 对象不是 Array,是一个类数组对象。因此你这么写`arguments,join()`（面试有被问到能不能这样）是会报错的，报`TypeError: arguments.join is not a function`.arguments 除了`length`和索引元素（`arguments[0]`这样写没问题，还可以设置它的值）外，没有任何数组的属性。`join`是数组才有的方法，因此报错。

以下方法可以将`arguments`转为真正的数组。

```javascript
let arg = Array.prototype.slice.call(arguments);
let arg = [].slice.call(arguments);
// es6
let arg = Array.from(arguments);
let arg = [...arguments];
```
