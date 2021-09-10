* 对vue来说模版的本质就是字符串
* 模版最终会转换成 `js` 代码，因为模版中有 `v-for`, `v-if`
* 模版会生成 `render` 函数，`render` 函数中包含所有的模版信息

* 模版转换为AST语法树
* AST语法生成 render 函数中with语法
* render函数返回的是vnode对象
* 其他函数（update）将vode渲染成html

* updateComponent

```js
vm._c 创建DOM标签
vm._v 创建文本节点
vm._s 
```
### render函数处理v-for
