# 关于webpack的alias
alias用于设置绝对路径的别名。
> 在vue-cli搭建的项目默认`@`是指向`src`。

如果需要额外配置,如下方式配置：
```js
 chainWebpack: (config) => {
    config.resolve.alias.set('src', path.join(__dirname, 'src'))
      .set('static', path.join(__dirname, 'src/assets'))
  },
```
## 非js文件
在非js文件中引用,因为字符串默认会被视为绝对路径解析，导致无法识别配置的别名，如下
```js
 @import "static/style/theme"
 background: url("static/assets/xxx.jpg")
 <img src="static/assets/xxx.jpg" alt="alias">
```
### 解决方法
在引用别名的字符串前面加上`~`，Webpack 会将以 `~` 符号作为前缀的路径视作依赖模块而去解析。
``` js
css module 中： @import "~static/style/theme"
css 属性中： background: url("~static/assets/xxx.jpg")
html 标签中： <img src="~static/assets/xxx.jpg" alt="alias">
```