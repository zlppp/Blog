
### 问题 ###
定义的公共less变量，需要在页面中引入才可以使用

```javascript
// 安装style-resources-loader
npm i style-resources-loader
```

```javascript
// vue.config.js
module.export =  {
  chainWebpack: config => {
    const types = ['vue-modules', 'vue', 'normal-modules', 'normal']
    types.forEach(type => addStyleResource(config.module.rule('less').oneOf(type)))
  }
}


function addStyleResource (rule) {
  rule.use('style-resource')
    .loader('style-resources-loader')
    .options({
      patterns: [
        // 全局less变量路径
        path.resolve(__dirname, './src/assets/styles/variable.less')
      ]
    })
}

```