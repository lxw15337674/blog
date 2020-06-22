# npm常用命令
[npm命令官方文档](https://docs.npmjs.com/cli-documentation/)
## install

### 语法
```
    npm install 或npm i
```
### 参数
```
-g、--global：视为全局的包，安装在系统预设的目录中。
-S、--save、:将模块保存在dependencies(生产环境依赖)。
-D、--save-dev:将模块保存在devDependencies（开发环境依赖）
-O、--save-optional ：将模块保存在optionalDependencies（可选环境依赖）。
-E、--save-optional：表示模块的版本是精确指定的。
-B、--save-bundle：表示将模块保存在bundleDependencies（构建依赖）。
```
