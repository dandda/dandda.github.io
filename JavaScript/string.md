> javascript 中的字符串是不可改变的。任何对字符串的操作，都不会改变原字符串，而是创建了一个新的字符串。

#### 字符串常用方法

#### 1. charAt(index)

index:下标,字符在字符串中的下标。返回指定位置的字符。

```javascript
let s = "love&peace";
s.charAt(4); //&
s.charAt();

//访问字符串中的字符，跟访问数组中的元素是一样的
console.log(s[2]); // 2

"love"[3]; //e
"love".charAt(3); //e
```

#### 2. charCodeAt(index)

返回指定位置的字符的 unicode 编码，范围为 0 ～ 65535 之间的整数。

```javascript
let s = "hello你好";
s.charCodeAt(5); //20320
s.charCodeAt(1); //101
```

#### 3. concat(string1,string2,string3,....)

> 实际开发中，一般使用字符连接符（+），更简洁。

```javascript
let s = "你好";
let newString = s.concat("呀", "未来");
console.log(newString); //'你好呀未来'
```

#### 4. s.indexOf(seachValue,fromIndex)

seachValue:要查找的字符

fromIndex:可选的整数参数。下标，合法范围 0 ～ s.length-1.

```javascript
let s = "abcdfabtylua";
s.indexOf("ab"); //0
s.indexOf("ab", 6); //-1,不存在。要匹配‘ab’,两个字符一起.
s.indexOf("ab", 6); //11
```

#### 5. s.lastIndexof(seachValue,formIndex)

seachValue:同 indexOf().

formIndex:可选，在字符串的指定位置从后往向前查找。

```javascript
let s = "luandluhailu";
s.lastIndexOf("lu"); //10
s.lastIndexOf("lu", 6); //5
```

#### 6. s.substring(start,stop)

提取介于两个指定位置的字符串。

start:必需。非负整数。

stop:可选，不包括该位置的元素。

```javascript
let s = "ilove汉口二厂汽水";
s.substring(5); //汉口二厂汽水
s.substring(5, 7); //汉口
```

#### 7. s.substr(start,length)

start:要截取的起始下标。

length:要截取的字符串个数。

```javascript
let s = "ilove汉口二厂汽水";
s.substr(5); //汉口二厂汽水
s.substr(5, 7); //汉口二厂汽水
```

#### 8. s.slice()

> 同 substring()使用方式一样，不过 slice()的参数可以为负数。

```javascript
let s = "ilove汉口二厂汽水";
s.slice(0, 5); //ilove
s.slice(-2); //汽水
```

#### 9. s.toUpperCase()

##### 将所有小写字母转换为大写字母，不是小写字母就原样输出。

```javascript
let s = "Ilike果汁汽水andCats";
s.toUpperCase(); //'ILIKE果汁汽水ANDCATS'
```

#### 10 s.toLowerCase()与 toUpperCase()相反，将所有大写字母转成小写字母。

#### 11 s.trim(),去除字符串首尾中所有的空格。字符串内部的空格不作处理

```javascript
let s = "\n \t\t come  true \t\n";
s.trim(); //'come  true'
```

#### 12. s.split(separator,limit)

separator:以什么来拆分，比如按照空格来拆，或者其他。

limit:返回的结果的个数。

```javascript
let s = " i like 汉 口 二 厂 汽水";
s.split(" "); //['i','like','汉','口','二','厂','汽水']
"like".split(""); //['i','l','k','e']

//使用场景比较多的就是将url的参数通过这个方法截取下来。
```

#### 13. s1.localeCompare(s2)

> 如果字符串(s1)在字母表中排在参数(s2)之后，则返回 1
>
> 如果字符串(s1)在字母表中排在参数(s2)之前，则返回-1
>
> 如果字符串(s1)等于参数(s2)，则返回 0

```javascript
let s1 = "b";
s1.localeCompare("aa"); //1
s1.localeCompare("dd"); //-1
```

> 用本地特定的顺序来比较两个字符串
>
> 1. s1.localeCompare(s2,'zh')
>
> 按照中文拼音的顺序排序比较.'zh'可选参数，表示语言环境
>
> 2. s1.localeCompare(s2,'en')
>
> 则是按照英文字母顺序排序比较
