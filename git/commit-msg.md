git 提交代码时，都要写 commit message(提交说明)。

```
git commit -m ''
```

`-m`参数后面就需要写提交信息（commit message）。

提交信息一行不够的写。可以只写 `git commit`，按下 enter 键会自动带出`vim`编辑器。这样就可以在编辑器写多行提交信息。

> vim 编辑器有关操作

1. 输入小写字母`i`,进入编辑模式。

2. 输入完毕，按`esc键`，此时退出编辑模式，输入英文输入法的冒号`:`，再输入`wq`即可保存退出。

目前规范使用较多的是 Angular 团队的规范,所以就讲这个规范。

> commit Message 格式如下：

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>

```

可以看上面结构。主要分为三个部分 Header,Body,Footer（以空行分开）。

1. Header：必写。type（提交类型），scope 影响范围。（可不写），subject:对改变的描述（必写）。
2. Body：对本次 commit 详细描述,（可不写）
3. Footer:只用于不兼容变动和关闭 Issue（可不写）

因为一般 Body 和 Footer 不写。下面就只讲 Header.

Header 部分只有一行。包括三个字段：type,scope,subject.

> type

一般七种类型

1. feat:新功能

2. fix：修补 bug
3. docs：文档
4. style：格式（不影响代码的变动）
5. refactor：重构（既不增加新功能，也不修改 bug）
6. test：增加测试
7. chore：构建过程或辅助工具的变动

> scope（一般不写）

用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

> subject

描述不超过 50 字符。

1. 以动词开头，用第一人称现在时。
2. 第一个字母小写
3. 结尾不写句号（.）

#### [写出好的 commit message](https://ruby-china.org/topics/15737)

#### [Commit message 和 Change log 编写指南](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

#### [优雅的提交你的 Git Commit Message](https://juejin.im/post/5afc5242f265da0b7f44bee4)

#### [约定式提交](https://www.conventionalcommits.org/zh-cn/v1.0.0-beta.4/)
