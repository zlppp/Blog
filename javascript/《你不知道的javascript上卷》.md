### 1、作用域
* 源代码在执行前会经历的三个步骤
* 分词/词法分析
  * 字符组成的字符串分解成有意义的代码块（词法单元）
* 解析/语法分析
  * 生成抽象语法树（AST)
* 代码生成
  * 将AST转换为可执行代码的过程称为代码生成

* 引擎：执行javascript
* 编译器：
* 作用域：变量或函数可以访问的范围

作用域链：
引擎从当前作用域开始查找变量，如果找不到，就会向上一级继续查找。
当抵达最外层的全局作用域时，无论是否找到，都会停止

函数作用域
属于这个函数的全部变量都可以在整个函数的范围内使用及复用 