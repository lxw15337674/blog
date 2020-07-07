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
3. webpack设置文件后缀补全。

在ts文件中引入其他ts文件会提示不能以'.ts'扩展名结尾。
>TS2691: An import path cannot end with a '.ts' extension. Consider importing './math' instead.
>
但webpack默认不会补全ts文件，就会在浏览器报错。
```js
// vue-cli默认补全后缀
[ '.mjs','.js',  '.jsx','.vue',  '.json','.wasm']
```
解决办法：配置webpack的扩展名处理。
```
resolve: {
        extensions: ['.ts', '.mjs','.js',  '.jsx','.vue',  '.json','.wasm']
    },  
```