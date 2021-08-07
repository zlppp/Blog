### BFC
* 创建一个独立的区域
* 普通文档流，两个元素的margin会重叠（取较大的高度），创建BFC后margin不会重叠

### 触发BFC
* overflow不为visible
* float不为none
* position为absolute或flex
* display为inline-block,table-cell,flex,table

BFC作用：
* margin不会重叠
* 清除浮动