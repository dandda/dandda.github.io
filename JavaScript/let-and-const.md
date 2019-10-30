#### let

块级变量声明，所声明的变量只在 `let` 命令所在的代码块内有效

1. 不存在变量提升(变量提升：变量可以在声明之前使用)

2. 暂时性死区

   区块中只要存在`let`和`const`命令，这个区块对这些命令声明的变量，就形成了封闭作用域。凡在声明之前使用这些变量，就会报错。

3. 不允许重复声明

#### const

1. const 关键字声明变量时，必须有个初始值，否则会报错。
2. const 声明的变量不可以通过再赋值修改,会报错。

```javascript
const a = 5;
a = 9; //Uncaught TypeError: Assignment to constant variable.
```

3. const 定义的常量并非真正的常量。定义的数组或对象是可以改变的，可以改变（包括修改和添加）数组里的元素和对象里的属性。但是对数组和对象再赋值依然是不可以的

```javascript
const arr = [1, 2, 4];
arr[2] = 8;
console.log(arr); //[1,2,8]

//不可以再赋值
arr = [2, 3]; ////Uncaught TypeError: Assignment to constant variable.
```

4. 具有`let`一样的属性。
