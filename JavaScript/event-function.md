事件是指用户或者浏览器自身执行的某种动作。执行事件的函数叫事件处理程序，事件处理程序的名字以`on`开头

分以下三种事件处理程序

- ###### html 事件处理程序

是在元素标签中添加的事件处理程序（也叫方法）,例子如下：

```
 <button onclick='showMessage()'></button>
<script>
function showMessage(){
  alert('hello')
}
</script>
```

**缺点：  
1.时差问题。在页面解析`showMessage()`函数之前，用户点击了按钮，这时页面会报错，解决方法是封装在一个`try-catch`块中；  
2.html 与 js 的代码紧密耦合（联系密切，不可分割），如对该方法修改函数名的话得同时改 html 和 js 两个地方，不方便**

- ###### dom0 级事件处理程序

是通过 js 给元素添加方法，如下

```
 <button id='btn'></button>
<script>
 var btn = document.getElementById('#btn')

 btn.onclick = function (){
  alert(2)
  //移除
 //btn.onclick = null
 </script>
```

**好处：简单，跨浏览  
缺点：元素只能绑定一个方法**

- ###### dom2 级事件处理程序
  每个元素都可以添加的方法。**addEventListener()**，这个方法有三个参数，第一个参数为事件名称，第二个参数为事件处理程序，第三个参数为 Boolen 值，`true`表示在事件捕获阶段执行事件处理程序，`false`,表示在事件冒泡阶段执行事件处理程序，如下

```
<script>
var btn = document.getElementById('#btn')
function myClick(){
  alert(2)
}
btn.addEventListener('click',myClick,false)
//移除，三个参数必须一模一样
//btn.removeEventListener('click',myClick,false)
</script>
```

**好处：可以添加多个事件。  
缺点:如果第二个参数为匿名函数是无法移除的，因为匿名函数在添加和移除的时候是不一样的**
