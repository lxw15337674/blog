# import和require引入问题
组件的一个需求是通过传递图片路径，设置组件的背景，最开始使用`require`来导入图片，如下
```js
 computed: {
    titleBg() {
      return {
        backgroundImage: `url(${import(this.imageSrc)})`
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
通过查资料后，了解到`require`不支持动态导入文件，需要使用`import`动态导入。