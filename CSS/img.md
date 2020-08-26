在处理图片遇到无法解决的问题时。或许给 img 加个时间戳可以解决。加时间戳可以使浏览器在规定时间里清除 img 缓存。

```
img.src = url + '?time=' + new Date().valueOf();

//or

<img src ='链接?v=1000000'>
```
