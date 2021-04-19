### css 的命名规范与准则

> 网上搜索相关的内容，大都没有很统一的一个标准，要根据项目大小，团队情况，个人习惯等等自己定制适合自己的这样的一套 css 系统，对适合，网上的方法只能参考，有些方法要适度用，就是在合适的地方要用合适的方法，太难了.jpg。

#### 命名方法

1. 面向对象的 css

例如，button 元素的样式可能是通过给出类的两个类来设置的：
<br>.button - 提供按钮的基本结构
<br>.grey-btn - 应用颜色和其他视觉属性

```css
.button {
  box-sizing: border-box;
  height: 50px;
  width: 100%;
}
.grey-btn {
  background: #eee;
  border: 1px solid #ddd;
  box-shadow: rgba(0, 0, 0, 0.5) 1px 1px 3px;
  color: #555;
}
```

2. BEM 命名语法

```css
/* 该.loginform 块由三个元素组成： */
.loginform__username
  输入用户名
  .loginform__password
  输入密码
  .loginform__btn
  允许用户提交
  Web
  表单
  三个修饰符是：
  .loginform__username--error
  出现错误时，会修改元素的可视属性，以便向用户显示错误。
  .loginform__btn--inactive
  修改元素的可视属性，使其具有非活动外观。
  .loginform--errors;
```
