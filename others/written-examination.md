1. `Array.isArray(Array.prototype)` ,返回 `true`.
2. `Object.prototype.toString.call(obj) === [object Array]`
3.

`['1','2','3'].map(parseInt)` 返回值为`[1,NaN,NaN]`.
解析：相当于 `['1','2','3'].map( (item,index,arr) =>{ return parseInt(item,index) })`
具体参考 [https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/4]里的 sisterAn 的回答。

4. ```javascript
   let arr = [1, 2, 3];
   arr[10] = 10;
   console.log(arr); //[1, 2, 3, empty × 7, 10]
   let newArr = arr.filter((i) => {
     console.log(i); //[1,2,3,10],empty会被忽略
     return i === undefined;
   });
   console.log("arr", newArr); // [],最终返回空数组
   ```
5. ```js
   let a = {},
     b = Object.prototype;
   console.log(a.prototype === b); //考察继承和原型，这都不是很懂。
   ```

6.生成随机字符串（每次长度一样）

```js
// 方法一
function randomString(len) {
  // 字符串的长度
  len = len || 32;
  let t = "ABCDEFGHJKMNPQRSTWXYZabcdefhijkmnprstwxyz2345678",
    a = t.length,
    newString = "";
  for (let i = 0; i < len; i++) {
    // Math.random()表示从0-1之间的随机数(包括0，不包括1)。charAt()字符串方法，返回指定位置的字符
    newString += t.charAt(Math.floor(Math.random() * a));
  }
  return newString;
}
let re = randomString(8);
console.log("re", re);

// 方法二
// .toString(36) 转化成36进制
//.slice(-6);截取最后八位。
let str = Math.random().toString(36).slice(-6);
console.log("str", str);
```

7.统计字符串中的每个字符的个数

```js
let str = "aaaaggkkkkkkktttkt";

// 方法一:使用对象
function count(str) {
  let obj = {};
  str.replace(/[a-z]/g, (i) => {
    !obj[i] ? (obj[i] = 1) : obj[i]++;
  });
  console.log("obj", obj);
}
count(str);

// 方法二：将字符转成数组

            var text = "";
            //循环的套出每个字符出现的次数 str会慢慢的变短直到为空
            while (str != "") {
                //先将字符转成数组
                // var newstr = str.split("");
               var newstr = [...str]
                var count = 0;
                //求得第一个字符出现的次数
                for (var i = 0; i < newstr.length; i++) {
                    if (newstr[0] == newstr[i]) {
                        count++;
                    }
                }
                //在字符串中删掉跟第一个字符一样的所有字符
                var re = new RegExp(newstr[0], "g");
                str = str.replace(re, "");
                text += newstr[0] + ":" + count + "次;";
            }
            console.log('text',text);
            return text; //我这里返回的是一段文本 可以自己改写成自己想要的形式
        }
        numInstring(str)
```
