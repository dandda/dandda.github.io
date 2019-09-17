##### 浅复制:

浅复制是`复制引用`，复制后的 引用类型数据 与原引用类型数据 都指向原实例（同一个堆），所以对其中任何一个操作都会影响另外一个。

##### 深复制:

深复制是`复制实例`，复制的实例是新开辟了一个堆区，并且把原实例的所有属性都进行新建复制，两个之间互不影响。

#### 浅复制的 case

```js
let obj = { a: 1, b: 2 };
// 扩展运算符
let copy = { ...obj };
```

```js
let obj = { a: 1, b: 2 };
let copy = Object.assign({}, obj); // {a:1,b:2}
```

```js
function shallowCopy(target, source) {
  for (let key in source) {
    target[key] = source[key];
  }
}
let stu = {
  name: "li",
  sex: "boy",
  skill: {
    sing: "good",
    dance: "excellent"
  }
};
let stu1 = {};
shallowCopy(stu1, stu);
stu1.skill.sing = "bad";
console.log(stu.skill.sing);
```

#### 深复制的方法

- 使用第三方库，如 `loadsh`,jquery 的`$.extend(true, {}, ...)`.
- 用 JSON.stringify()和 JSON.parse()

  这个方法处理的数据必须是可序列化，例如 Date 对象就无法处理。还有处理的时候会把所有函数和原型成员丢失。

- 使用递归

```javascript
function deepClone(obj) {
  var copy;

  // Handle the 3 simple types, and null or undefined
  if (null == obj || "object" != typeof obj) return obj;

  // Handle Date
  if (obj instanceof Date) {
    copy = new Date();
    copy.setTime(obj.getTime());
    return copy;
  }

  // Handle Array
  if (obj instanceof Array) {
    copy = [];
    for (var i = 0, len = obj.length; i < len; i++) {
      copy[i] = deepClone(obj[i]);
    }
    return copy;
  }

  // Handle Function
  if (obj instanceof Function) {
    copy = function() {
      return obj.apply(this, arguments);
    };
    return copy;
  }

  // Handle Object
  if (obj instanceof Object) {
    copy = {};
    for (var attr in obj) {
      if (obj.hasOwnProperty(attr)) copy[attr] = deepClone(obj[attr]);
    }
    return copy;
  }

  throw new Error(
    "Unable to copy obj as type isn't supported " + obj.constructor.name
  );
}
```

<https://smalldata.tech/blog/2018/11/01/copying-objects-in-javascript>
