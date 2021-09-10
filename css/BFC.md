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


### 伪类和伪元素的区别
* 区别：是否有创建元素
* 伪元素会创建虚拟元素，不在文档树中
  * `:before` \ `::before` 
  * `:after` \ `::after`

* 伪类存在dom文档中，
  * `:link`
  * :active
  * hover、visited、focus、first-child、last-child、first-of-type、last-of-type