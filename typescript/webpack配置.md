# webpack配置
无意间想到应用TS的最佳场景就是写各种公共方法，正好新项目开整，直接搞起。
1. 安装两个模块
```
npm i -D typescript ts-loader 
```
2. 添加ts的配置文件`tsconfig.json`,详细配置可以参考[tsconfig.json编译选项](https://juejin.im/post/5baae25d5188255c68158611)
```
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es5",
    "sourceMap": true
  },
  "exclude": [
    "node_modules"
  ]
}
```
