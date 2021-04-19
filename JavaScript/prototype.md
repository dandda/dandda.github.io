###### 概念

声明一个函数的时候，函数有个默认的属性`prototype`指向一个对象。这个对象就是函数的原型对象。简称函数的原型。

##### 构造函数创建对象

> 所有函数都可以是构造函数，按照惯例，构造函数名首字母一般大写。使用`new`操作符操作函数就可以创建一个对象。

```js
function Person() {}
var p1 = new Person();
//new创建出来的对象(例如p1)，有一个不可见的属性[[prototype]]指向构造函数的原型对象即Person.prototype
```

##### 原型相关方法和属性

###### 1.instanceOf 操作符

> 判断对象类型

```js
function Person(){

}
var p1 = new Person()
console.log(p1 instanceOf Person ) //返回true
// 对象p1是否是Person类型的对象。
```

###### 2.hasOwnPropety()方法

> 判断某个属性或方法是不是对象本身里的。唯一一个处理属性不会查找原型链的方法

```js
function Student() {
  this.name = "晓霞";
  this.age = "18";
}
Student.prototype.sex = "girl";
var stu = new Student();
console.log(stu.hasOwnProperty("name")); //在对象本身return true
console.log(stu.hasOwnProperty("sex")); //在原型 return false
console.log(stu.hasOwnProperty("work")); //不存在的属性 return false
//可以看出hasOwnProperty()方法无法判断属性是不存在还是在原型中。
```

###### 3.in 操作符

> 用来判断一个属性是否存在于对象或者对象的原型中。如果都不存在则返回 false。

```js
function Student() {
  this.name = "晓霞";
  this.age = "26";
}
Student.prototype.sex = "girl";
var stu = new Student();
console.log("age" in stu); //true
console.log("sex" in stu); //true
console.log("work" in stu); //false
// 可以看到依然不能判断一个属性是在对象中还是在对象的原型中。但是还有个hasOwnProperty()。可以结合两者就能解决是在对象中还是原型中的问题
function propertyLocation(obj, prop) {
  if (!prop in obj) {
    return "该属性不存在";
  } else if (obj.hasOwnProperty(prop)) {
    return "该属性在对象中";
  } else {
    return "该属性在原型中";
  }
}
```

> 题外：in 操作符也可以用来操作数组。
> 语法：index in arr

```js
var arr = ["app", "banana", "fruit", "peach"];
arr[0] = null;
// 判断数组元素是否有值。数组元素只为空插槽（empty）或者不存在就返回false,其它都返回true，unll,undefined,''也都返回true.
console.log(0 in arr); // true
```

###### 4.属性

4.1 prototype

> 指向构造函数的原型。

4.2 constructor

```js
function Student() {}
console.log(Student.prototype.constructor === Student); //true
Student.prototype = {
  duty: function () {
    console.log("to study");
  },
};
console.log(Student.prototype.constructor === Student); //false
//此时的Student.prototype.constructor指向的是Object()构造函数
Student.prototype = {
  constructor: Student,
};
console.log(Student.prototype.constructor === Student); //true
```

> 上述代码中给构造函数`Student`的原型重新赋值一个对象，这个新的原型对象的`constructor`属性值就不再指向构造函数 Student.如果需要用到`constructor`,就要重新指回 Student.

4.3 `__proto__`

> 注意是双下划线。是 new 构造函数创建的对象才有的属性.这个属性`[[prototype]]`是不可访问的。但是个别浏览器可以通过`__proto`访问，开发者尽量不要这样访问。该属性指向构造函数的原型。

```js
function Person() {}
var p1 = new Person();
console.log(p1.__proto__ === Person.prototype); //true;
```

##### 组合使用原型模型和构造函数模型创建对象

1.原型模型创建对象的缺点

> 原型所有的属性和方法都是共享的。构造函数创建多个对象，多个对象访问原型的属性时，访问的原型都是一样的。如果其中一个对象修改了原型的属性，会反映到其它对象上。

2.构造函数模型创造对象的缺点

> 构造函数里的属性和方法都是不共享的。于对象来说，属性一般私有，方法可以共享。因此结合原型模型和构造函数模型完美解决各自的缺点。

3.组合模型

> 在构造函数里定义属性，原型定义方法

```js
function Person() {
  this.name = "小李";
  this.age = 26;
}
Person.prototype.eat = function () {
  console.log("我吃完啦");
};
```

4.动态组合模型
