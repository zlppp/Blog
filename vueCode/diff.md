### diff算法
* 操作真实dom是非常消耗性能的，diff可以帮助我们只更新我们修改的那一小块dom。

* diff的过程就是调用path函数比较新旧节点，一边比较一边给真实dom打补丁
### 当数据变化时，vue是怎么更新节点的？
* 根据真实 dom 生成 Vnode，当 Vnode 某个节点数据改变就会生成一个新 Vnode，然后 oldVnode 和 Vnode 会进行比较，发现不一样的地方就直接修改在真实 dom 上，然后使 oldVnode 的值为 Vnode

### diff算法的比较方式
* 只会比较同级节点，不会跨层比较。
* 1、 sameVnode 判断新旧节点是否值得比较，如果不一致则直接替换oldVnode
```JS
 function sameVnode (a, b) {
   return {
     a.key === b.key && // 比较key是否相同
     a.tag === b.tag && // 比较tag是否相同
     a.isComment === b.isComment && // 比较是否为注释节点
     isDef(a.data) === isDef(b.data) && // 是否都定义了data，data包含onClick，style等
     sameInputType(a, b) // 当标签是input时，type必须相同

   }
 }
```

* 2、如果节点值得比较，则会对节点指定 pathVnode 方法
  * pathVnode
    * 判断Vnode是否有text，有则，比较text是否相同，添加新的text或者更新text 并删除oldVnode的children
    * Vnode无text，有children
      * oldVnode有children，更新children需调用updataChildren
      * oldVnode有text
        * 清除旧的text，添加新的children或更新children

```js
  // child和text互斥
  // 新vnode无text 有child
  if (isUndef(vnode.text)) {
    // oldVnode 有child && vnode有children
    if (isDef(oldCh) && isDef(ch)) {
      // 不相同则需要调用updateChildren方法
      if (oldCh !== ch) updateChildren(elm, olcCh, ch, insertedVnodeQueue)

    // vnode有children，oldvnode无children有text
    } else if (isDef(ch)) {
      // 清空text
      if (isDef(oldVnode.text)) api.setTextContent(elm, '')
      // 添加children

    // 新vnode无children， oldVnode有children
    } else if (isDef(oldCh)) {
      // 移除oldVnode children
      removeVnodes(elm, oldCh, 0, oldCh.length - 1)

    // oldVnode有text
    } else if (isDef(oldCh.text)) {
      // 清空text
      if (isDef(oldVnode.text)) api.setTextContent(elm, '')
    }

  // 新vnode有text，无child
  // 老vnode 不等于 新vnode
  } else if (oldVnode.text !== Vnode.text) {
    // 将新的vnode的值赋值给oldvnode
    // 移除oldvnode的child
    ...
  }
```

参考链接https://juejin.cn/post/6844903607913938951