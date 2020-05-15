在处理图片遇到无法解决的问题时。或许给 img 加个时间戳可以解决。貌似加时间戳清除 img 缓存。
img.src = url + '?time=' + new Date().valueOf();
