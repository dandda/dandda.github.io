---
插件：[⏰ Day.js 2KB immutable date library alternative to Moment.js with the same modern API](https://github.com/iamkun/dayjs)
---

### 获取时间戳(毫秒)的方法

#### 1. `+new Date()` 使用操作符

#### 2. `Date().now` es5 才添加的方法

#### 3. `new Date().getTime()`

#### 4. `Date.parse(new Date())` 这个是把毫秒之后的数字一律换成 0。也就是只精确到秒。

#### 5. `new Date().valueOf()`

---

> 一般获取日期。都是比较记得`getFullYear(),getMonth()`(ps:getMonth()是从 0 开始的).但也别忘了`setFullYear()`等设置时间的方法。
