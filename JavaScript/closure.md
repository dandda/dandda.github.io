闭包：里边的函数可以访问其外边函数的作用域
关于一些闭包的问题

```js
for (var i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log(i);
  }, 100 * 1);
}
// 想要输出0，1，2，3，4，结果却输出5次5.

// 解决方法一：var声明的i是全局变量，使i被不断覆盖。把 var 改成let
// 方法二：将变量i作为参数传到闭包中，闭包使这5个`i`独立，使`i`在当前循环有效，每一次循坏的i都是一个新的变量。
for (var i = 0; i < 5; i++) {
  (function (i) {
    setTimeout(function () {
      console.log(i);
    }, 100 * 1);
  })(i);
}
// 方法三：赋值给一个变量存起来
for (var i = 0; i < 5; i++) {
  (function () {
    var s = i;
    setTimeout(function () {
      console.log(s);
    }, 100 * 1);
  });
}
```
