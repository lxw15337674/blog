# 利用require.context()自动化导入
## 痛点
如果页面需要调用多个组件时，需要写大量重复代码进行声明，如下：
```
import topTitle from "./components/top-title";
import todayEvent from "./components/todayEvent";
import baseData from "./components/baseData";

 components: {
    topTitle,
    eventRank,
    baseData
  },
```

## 解决办法
利用`webpack`提供的API`require.context()`创建自己的上下文,实现自动化导入。
> [webpack官方文档](https://webpack.js.org/guides/dependency-management/#require-context）)：
可以使用require.context()函数创建自己的上下文。
它允许传入要搜索的目录、指示是否也应该搜索子目录的标志和用于匹配文件的正则表达式。webpack在构建时在代码中解析require.context()。

>

#### require.context 语法
参数 | 说明 | 类型 | 
---|---|---|---|---|---
resolve | 要读取的文件路径 | Array、String | 
keys | 是否遍历子目录| Boolean| 
id | 匹配文件的正则表达式| regExp|

```js
//示例
 require.context("./components", false, /\.vue$/)
```

require.contenxt()的返回值并不是如预期一样返回遍历的文件对象，而是返回一个函数，如下：
```js
var map = {
	"./baseData.vue": "./src/views/components/baseData.vue",
	"./todayEvent.vue": "./src/views/components/todayEvent.vue",
	"./top-title.vue": "./src/views/components/top-title.vue"
};


function webpackContext(req) {
	var id = webpackContextResolve(req);
	return __webpack_require__(id);
}
function webpackContextResolve(req) {
	if(!__webpack_require__.o(map, req)) {
		var e = new Error("Cannot find module '" + req + "'");
		e.code = 'MODULE_NOT_FOUND';
		throw e;
	}
	return map[req];
}
webpackContext.keys = function webpackContextKeys() {
	return Object.keys(map);
};
webpackContext.resolve = webpackContextResolve;
module.exports = webpackContext;
webpackContext.id = "./src/views/components sync \\.vue$";
```

通过阅读可以看到需要使用`keys`属性，来得到文件名数组。

``` JS
components.keys().forEach((fileName) => {
    console.log(fileName)
}

/* 输出结果
'./community.vue'
 './todayEvent.vue'
'./top-title.vue'
*/
```
这时还不是我们想要的模块，需要将文件名带入返回的方法中，得到真正的modules，再通过modeles的default获得导出的默认模块，如下：
```js
const components = require.context("./components", false, /\.vue$/)
const modules={}
components.keys().forEach((fileName) => {
    components(fileName).default 
});

/* 输出结果
{name: "baseData", staticRenderFns: Array(1), _compiled: true, data: ƒ, render: ƒ, …}
{name: "community", staticRenderFns: Array(0), _compiled: true, data: ƒ, render: ƒ, …}
{name: "todayEvent", staticRenderFns: Array(0), _compiled: true, data: ƒ, render: ƒ, …}
*/
```
此时才获得真正的模块，进行组件的声明,如下：
```js
const context = require.context("./components", false, /\.vue$/)
const modules={}
context.keys().forEach((fileName) => {
  const name = fileName.split('/')
          .pop()
          .replace(/\.\w+$/, '')
  modules[name]= context(fileName).default ||context(fileName)
});

components: ...modules
```
## 扩展
通过这个API可以打开新世界的大门，可以代替各种声明代码，例如：
1. 全局组件声明
```js
const context = require.context('./global-components', false, /\.vue$/);
context.keys().forEach((fileName) => {
    const componentConfig = context(fileName);
    const componentName = `g-${fileName
        .split('/')
        .pop()
        .replace(/\.\w+$/, '')}`;
    Vue.component(componentName, componentConfig.default);
});
```
2. vuex模块导入
```js
const context = require.context('./modules', true, /\.js$/);

const modules = context.keys().reduce((modules, modulePath) => {
  // set './app.js' => 'app'
  const moduleName = modulePath.replace(/^\.\/(.*)\.\w+$/, '$1');
  const value = context(modulePath);
  modules[moduleName] = value.default;
  return modules;
}, {});

export default new Vuex.Store({
  modules,
});

```

还有vue-router 动态添加路由等等，不再详细列举。

