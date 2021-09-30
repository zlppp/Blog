多个组件内有相同的业务逻辑，即可以将业务逻辑抽离出来，再使用mixin，混入代码
`mixins` 混入的钩子函数会优先于组件内的钩子函数执行

### 选项合并
- 数据对象会进行递归合并，发生冲突时以组件内优先
- 同名钩子函数将合并为一个数组，都将被调用，混入对象钩子函数先调用
- 值为对象的选项，如 `methods`、 `components`, `directive`,合并为同一对象，被替换



替换型有`props`、`methods`、`inject`、`computed`新的同名参数替代旧的同名参数
合并型有`data`, 通过set方法进行递归合并
队列型有生命周期和`watch`将函数存入一个数组，然后正序遍历依次执行
叠加型有`components`、`directives`、`filters`，将回调通过原理链联系在一起

链接 https://cn.vuejs.org/v2/guide/mixins.html