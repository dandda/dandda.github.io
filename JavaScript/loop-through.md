作为一个菜鸡，使用过最多的就是最简单的`for`循环。虽然听过其他如`for...in`, `for...of`之类的，但几乎未使用过。现在呢在梳理这些遍历数组的方法时看了不少博客，才知道最简单的`for`循环，性能是最高滴，不枉我就只使用它（ 😂）。

<h3>遍历数组</h3>

<h4>1. forEach</h4>

`forEach(callback[, thisArg)`
回调函数的三个参数：循环出的每项，数组索引，原数组。
thisArg:当执行回调函数时用作 this 的值(参考对象)

优点：不需要声明索引和变量,但是不能使用`break`跳出循环，会报错`Error: Illegal break statement`.在判断条件里使用`return`,无法终止。

```javascript
let a = ["a", "b", "c"];
a.forEach(ele => {
  console.log(ele); // a b c
});
```

使用`forEach`可以对 对象 进行深复制。

```javascript
function copy(obj) {
  var copy = Object.create(Object.getPrototypeOf(obj));
  var propNames = Object.getOwnPropertyNames(obj);

  propNames.forEach(function(name) {
    var desc = Object.getOwnPropertyDescriptor(obj, name);
    Object.defineProperty(copy, name, desc);
  });

  return copy;
}

var obj1 = { a: 1, b: 2 };
var obj2 = copy(obj1);
```

<h4>2. for...in</h4>
 
`for...in`是用来循环对象的，一般不会用来循环数组的。其实也可以循环数组，只不过会有问题，其中一个就是不能保证循环数组的顺序。对于特殊的数组是有用的，比如 稀疏数组（sparse arrays）
```javascript
//'a' is a sparse array
let a = []
a[0]= 1
a[10]= 2
a[100000] = 3
// 用 for...in 只需循环三次，不需要100001次
for (let key in a) {
  if (a.hasOwnProperty(key)){
    console.log(a[key]) // 1    2    3
  }
}
```
<h4>3. for... of </h4>

要说缺点就是没有索引，除此之外简直无敌。可以迭代`map~`,`set~`,`arguments类数组对象`,`NodeList这类DOM集合`,还可以搭配`object.keys()`等使用

<h3>遍历对象</h3>

```javascript
const tree = {
  color: "greeen",
  breed: "arbor",
  name: "cedar"
};
```

<h4>1. for...in</h4>
<h4>2. Object.keys</h4>

```javascript
let arr = Object.keys(tree);
// 返回对象的属性名的一个数组集合
console.log(arr); //['color','breed','name']
```

<h4>3. Object.values</h4>

```javascript
let value = Object.values(tree);
console.log(value); //['green','arbor','cedar']
```

<h4>4. Object.entries</h4>

```javascript
const girl = {
  name:'coo',
  height:'168cm',
  sing(){
    console.log(111)
  }
}
// 返回键值对，返回的顺序不一定按照对象定义的顺序
for (let [key,value] of Object.entries(tree)) {
  console.log(key+':'+value)
  // name:coo
  // height: 168cm
  // sing:sing(){
    console.log(111)
  }
}
```
