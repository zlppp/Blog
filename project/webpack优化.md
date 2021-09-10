### tree shaking 消除无用js代码
* 通过Tree Shaking将没有使用的模块摇掉，减少代码体积
* 前提：1、必须使用es6模块；2、开启production环境


### ClearWebpckPlugin 清除无用文件
* `build` 之前将之前生成的文件清除

```js
  new ClearWebpackPlugin(['dist'])
```

### uglifyjs-webpack-plugin 压缩js代码
```js
const uglifyjsPlugin = require('uglifyjs-webpack-plugin')
module.exports = {
  optimization: {
    minimizer: [new uglifyjsPlugin({
      text: /\.js(\?.*)?$/i
    })]
  }
}
```

### html-webpack-plugin

### IgnorePlugin
* 可使用 IgnorePlugin 在打包时忽略本地化内容,只打包中文moment
```js
new webpack.IgnorePlugin('')
```

### code-split 代码分割
#### 多入口
```js
  module.export = {
    entry: {
      main: './js/main.js',
      test: './js/test.js'
    },
    ouput: {
      filename: 'js/[name].[contenthash:10].js'
    }
  }
````

* 