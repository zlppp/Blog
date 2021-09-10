### soure-map
* 便于调试，如果代码出错，通过映射可以追踪代码错误


### 懒加载
* 懒加载会进行代码分割
* 使用import ()

```js
document.getElementId('btn').onClick = function () {
  import (/* WebpackChunkName: 'test', webpackPrefetch: true */'./1.js').then(res => {

  })
}
```