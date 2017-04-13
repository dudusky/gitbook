# 编译原理

* 引擎

  从头到尾负责整个JavaScript代码的编译和执行.

* 编译器编译步骤

  * **语法分析** 例如将`var a = 10;` 分析为`var, a, =, 10`
  * **解析** ,  形成语法树(AST),  例如`var a = 10`的语法树为a的名称, a类型, a的值.
  * **代码生成**  : 例如`var a = 10;` 会分为两个步骤执行
    * var a;  引擎看到的是这样的, 只有声明, 没有赋值, 变量提升, 会提前到当前作用域的顶部.
    * a = 10; 赋值

* 作用域

  负责收集所有声明的标识符(变量名称), 确定当前执行的代码对这些标识符的访问权限.

编译过程还会对代码进行优化: 

例如会将以下代码编译成

```javascript
function fun() {
  console.log(a);
  var a = 10;
}
fun()


// 编译器看到的是这样的
function fun() {
  var a;
  console.log(a);
  a = 10;
}
fun()

```





编辑器解析过程: 
![](/assets/screenshot-medium.com-2017-04-13-15-06-53.png)








