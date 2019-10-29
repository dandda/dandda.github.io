使用命令 `npm shrinkwrap`会生成一个锁定文件`npm-shrinkwrap.json` ，
这样不管在什么地方拉取的项目依赖版本，都是一样的模块版本，防止拉取不一样的依赖模块（就是别人启用你的项目的时候会自动拉取最新的依赖模块）。

```
npm install --save or npm install -S 是程序运行所需要的包，即生产环境所需要的包。会保存到dependencies里

npm install --save-dev or npm install -D 是开发环境所需要的包，例如unit tests(单元测试)。会保存到 devDependencies里
```
