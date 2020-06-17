# require 动态引入问题
## 问题
开发中遇到一个需求：通过传递图片路径，设置组件的背景，最开始使用`require`来导入图片会报错，如下
```js
 computed: {
    titleBg() {
      return {
        backgroundImage: `url(${require(this.imageSrc)})`
      };
    },
  },
  props: {
    imageSrc: {
      type: String,
      default: "images/context-background/left-center.png"
    }
  }

// error
// Uncaught (in promise) Error: Cannot find module 'images/context-background/left-center.png'
  ```
通过查看[webpack官方文档](https://webpack.js.org/guides/dependency-management/#require-context）)关于require的动态导入:
>  如果 request 含有表达式(expressions)，会创建上下文(context)，导致在编译时(compile time)并不清楚具体是哪一个模块被导入。
>
## 分析原因
 webpack本身是一个预编译的打包工具，无法预测未知变量路径，因此不能require纯变量路径，目录前必须用常量声明（可以使用alias）。
## 解决办法
 参数使用路径+变量。修改如下：
```js
 computed: {
    titleBg() {
      return {
        backgroundImage: `url(images/${require(this.imageSrc)})`
      };
    },
  },
  props: {
    imageSrc: {
      type: String,
      default: "context-background/left-center.png"
    }
  }
```