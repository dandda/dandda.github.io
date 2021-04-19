1. `<input type='file'>`添加`multiple`属性可以同时上传多个文件，否则只能上传一个文件
   有一个问题：点击上传文件按钮，打开文件选择框，不选择文件，点击取消时，之前的选择的文件会自动被移除。这个问题只在谷歌浏览器中才这样。
   解决方法如下：

   ```js
   // 用chang事件监听
   let input = document.getElementsByTagName("input")[0];
   input.addEventListen("change", function () {
     var file = this.files[0];
     if (file) {
       // if file selected, do something
     } else {
       // 点击取消。直接return
     }
   });
   ```

2.FileReader 对象

3.FormData 对象
