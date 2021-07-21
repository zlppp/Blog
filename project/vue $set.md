
```js
let emptyIndex = this.form.list.findIndex(item => !item.shareMemberId)
if (emptyIndex !== -1) {
  this.form.list[emptyIndex] = {
    shareMemberId: selected.shareMemberId,
    sharePortion: this.form.list[emptyIndex].sharePortion
  }
} else {
  this.form.list.push({ shareMemberId: selected.shareMemberId })
}
```

vue不能检测对象属性的添加和删除