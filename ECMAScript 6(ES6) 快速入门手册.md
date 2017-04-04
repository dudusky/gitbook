# ECMAScript 6(ES6) 快速入门手册 

![](http://upload-images.jianshu.io/upload_images/1504317-805392e6d4ad6f43.jpg?imageMogr2/auto-orient/strip%7CimageView2/2)

by Rosa                                                                                                                                      
```
// 课堂案例
http://codepen.io/Rosa0205/

// 课程资料到本地
git clone https://github.com/dudusky/ES6_tutorial_demo.git
git clone https://github.com/dudusky/es6-tutorial.git
```


## 一. ECMAScript快速概览

> ES6的背景和概念 , 以及亮点.

###  1. 背景介绍

* ES6在2015年6月正式发布.
* ECMAScript是ECMA国际制定和发布的语言.
* JavaScript是ECMAScript的实现和扩展.
* ECMAScript 6.0 (简称 ES6/ES2015), 是 JavaScript(ES5)的下一代标准.
* ES7/ES2017会在明年发布.

### 2.  ES6的优势

> 解决了哪些ES5没有解决的问题(面试问题)?
* 语法简洁, 方便维护, 可读性高
* 作用域
* class类的继承
* 模块化


## 二. 如何开始使用ES6？

### 1. ES6的兼容和规范
* [目前主流浏览器对ES6的支持情况](http://kangax.github.io/compat-table/es6/)

* [检查当前浏览器的ES6支持情况](http://ruanyf.github.io/es-checker/)

* 检查当前Node环境对ES6的支持情况

  ```
  $ npm install -g es-checker
  $ es-checker
  ```

  ​

### 2.  ES6转码工具Babel使用方法

![](http://www.ruanyifeng.com/blogimg/asset/2016/bg2016012501.png)

>  Babel是一个ES6转码器, 可以将ES6代码转换为ES5代码.
>
>  好处是可以使用ES6的语法, 而不用担心当前的环境是否完全支持ES6.
>
>  例如使用箭头函数, Babel可以将其转换为普通函数, 就能在不支持ES6的环境中执行了.
>
>  Babel在线转换http://babeljs.cn/repl/


*In*
```javascript
//ES6 arrow function 
[1, 2, 3].map((n) => n + 1);
```

*Out*
```javasrcpit
[1, 2, 3].map(function(n) {
    return n + 1;
});
```

---
#### 1. 准备工作:

*  创建一个项目名为`babel_test`的文件夹.
  *  创建一个标准为ES6的js文件, 内容为`[1, 2, 3].map((n) => n + 1);`,  保存为`es6.js`.
  *  创建两个文件夹,分别名为`src`和`lib`.
  *  创建`package.json`文件和`.babelrc`文件(参见第三点).


----------


#### 2. 安装babel-cli命令行工具
> 在[node官网](https://nodejs.org/en/download/)安装node.js, 然后就可以使用npm包管理工具来安装babel-cli命令行工具

```JavaScript
  # 在项目目录如d:\babel_test\下安装babel-cli
  $ npm install --save-dev babel-cli

  # 安装最新的转码规则
  $ npm install --save-dev babel-preset-latest
```

----------


#### 3. 在项目目录下创建隐藏文件`.babelrc`文件和`package.json`文件(可选)

> 注意, 所有 Babel工具和模块的使用，都必须先写好`.babelrc`.

`pakage.json`配置内如下: 

```
{
  "devDependencies": {
    "babel-cli": "^6.0.0"
  },
  "scripts": {
    "build": "babel src -d lib"
  },
}
```
 `.babelrc`配置内容如下:

```
     {
        "presets": [
          "latest"
        ],
        "plugins": []
      }
```

----------

#### 4. Babel-cli的基本使用方法:
```    
    # es6.js为ES6代码 使用bable命令编译要转换的ES6代码
    $ babel es6.js
   
    # 使用-o指令 将转码结果写入到一个文件
    $ babel es6.js -o es5.js
    
    # 使用-d 将ES代码所在目录转码到另外一个目录
    $ babel src -d lib
    
    # 如果配置好package.json文件 可以使用以下快捷方式 等同于src -d lib
    $ npm run build
```

----------

#### 5. babel-polyfill 的使用

> babel-plyfull可以转换babel不能转换的语法.
> babel默认只转换JavaScript的语法, 而不转换新的 API, 比如`Iterator`, `Set`, `Maps`, `Promise`等全局对象.

* 安装如下

  ```
  $ npm install --save babel-polyfill
  ```

* 使用方式

  ```
  import 'babel-polyfill';

  //或者
  require('babel-polyfill');
  ```

---

### 3. 使用Webpack进行ES6开发

> Webpack是当前最热门的前端资源模块化管理和打包工具.

* 目标: 使用Webpack快速搭建可以使用ES6开发的项目


---
## 三. ES6实用新特性

> ES6开发中最常用语法介绍和案例.

### 1.  块级作用域 `let`和`const`

#####    let的特性

> * 块级作用域
> * 可以赋初始值, 也可以不用赋值.
> * 没有作用域提升
> * 暂时性死区(TDZ)

* 基本用法和常见错误

  ```JavaScript
  let myPet = "dog"

  if(ture) {
    let a = 10;
    var b = 1;
  }

  a // ReferenceError: a is not defined.
  b // 1

  //TDZ
  function add(a) {
    console.log(a) //ReferenceError: a is not defined a没有声明
    let a = 10
  }
  ```

* 作用域


  ```JavaScript
   var myVar = "golobal var"

   function fun() {
     console.log(`函数体顶部未声明前的var: myVar: ${myVar} `)

    var myVar = "function var"

    if(true) {
      var myVar = "block var"
       console.log(`if语句里的var:myVar: ${myVar}`)
    }
    
    console.log(`函数体底部声明后的var: myVar: ${myVar}`)

  }
   console.log(`全局作用域下的var: myVar: ${myVar} `)
   
    fun()
  ```


##### const的特性

> * 声明一个只读的常量, 赋值后常量的值就不能改变, 
> * 初始化必须赋值.
> * 常量名一般为大写字母.
> * 块级作用域.
> * 暂时性死区(TDZ)

- 基本用法和常见错误

  ```JavaScript
  const PI = Math.PI

  PI = 23 // TypeError: Assignment to constant variable / "PI" is read-only 不能重新赋值

  const MY_COLOR // SyntaxError: Missing initializer in const declaration 初始化需赋值

  //TDZ
  if (true) {
    console.log(MAX); // ReferenceError
    const MAX = 5; //必须先声明后使用
  }
  ```

  ​

- 代码演示:  由let, const, var声明的变量在不同情况下Global,  function,  Block的作用域

- 问题: `let`, `var`, `const`的区别有哪些? 它们有什么特定的使用场景?

  ​


---
### 2. 变量/参数的结构赋值

* 变量的结构赋值

```JavaScript
let singer = { first: "Bob", last: "Dylan" }; 

let { first: f, last: l } = singer;  // 相当于 f = "Bob", l = "Dylan"

let [x, y] = [1, 2, 3];  // x = 1, y = 2
```



* 函数参数的结构赋值

  ```JavaScript
  function add([x, y]) {
    return x + y;
  }
  console.log(add([2, 4])); //6
  ```

* 为函数参数设置初始值

  ```JavaScript
  //ES6参数赋值
  function f(x, y = 10, z = 20) {
    return x + y + z;
  }
  f(2) //32

  //ES5函数中的参数不能赋值
  function f (x, y, z) {
      if (y === undefined)
          y = 7;
      if (z === undefined)
          z = 42;
      return x + y + z;
  };
  f(1) //50
  ```

  ​


* Rest参数

  > 设置更多的参数作为一个数组(与类数组argument不同), 好处是可以使用数组方法.

  ```JavaScript
  function f (x ,y, ...restAr) {
    var a = restAr
    console.log(a) //array
    console.log(a.length) //4
    return console.log(((x + y) * a.length)) //12
  }
  f(1, 2, "hi", 9, 20, 55) 
  ```

  ​

* 数组参数

    ​    连接数组

  ```JavaScript
  //使用ES6
  var params = [ "hello", true, 7 ]
  var other = [ 1, 2, ...params ] // [ 1, 2, "hello", true, 7 ]

  //ES5写法
  var params = [ "hello", true, 7 ];
  var other = [ 1, 2 ].concat(params); // [ 1, 2, "hello", true, 7 ]
  ```


    将字符串字符分割转换为数组

  ```
  //使用ES6
  var str = "foo"
  var chars = [ ...str ] // [ "f", "o", "o" ] 

  //使用ES5
  var str = "foo"
  var chars = str.split("");  // [ "f", "o", "o" ]
  
  ```

---
### 3. 字符串扩展方法(模板字符串)

* 模板字符串(template string)

  > 用反引号标识(Esc键下方). 它可以当作普通字符串使用, 也可以用来定义多行字符串, 或者在字符串中嵌入变量.

  ```javascript
  // 普通字符串
  `In JavaScript '\n' is a line-feed.`

  // 多行字符串
  `In JavaScript this is
   not legal.`

  console.log(`string text line 1 string text line 2`);

  // 字符串中嵌入变量
  var name = "Bob", time = "today";
  `Hello ${name}, how are you ${time}?`

  //在模板字符串中使用反引号, 需要使用反斜杠转义
  var greeting = `\`Yo\` World!`;
  ```

* 案例

    ```javascript
     // 使用模板字符串拼接字符串
     var customer = {name: "Ros"};
      var friut = {
    			amount: 10,
    				tag: "apple",
    				price: 5
     			 };

      var message = `你好! ${customer.name},
      你要买${friut.amount}个${friut.tag}对吗?
      一共是${friut.amount * friut.price}元`
    ```



* `repeat(number)`

  > 返回一个新字符串, 表示将原字符串重复 n 次.

  ```javascript
  "abc".repeat(2) //"abcabc"
  ```

---

### 4.  数组扩展方法

#### Array.from()

> 用于将可遍历的对象转为真正的数组

* 基本用法

  ```JavaScript
  // 将一个类数组对象转换为数组
  let arrayLike = {
      '0': 'a',
      '1': 'b',
      '2': 'c',
      length: 3
  };

  // ES5的写法
  var arr1 = [].slice.call(arrayLike); // ['a', 'b', 'c']

  // ES6的写法
  let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
  ```

  ​




### 5. Set和Map数据结构

#### Set

> Set类似于数组, 区别是内部成员的值不能重复.
>
> Set是一个构造函数,可以创建Set数据结构.
>
> Set实例的操作数据的方法: add(value), delete(value)
>
> Set实例的遍历方法之一: `forEach()` 使用回调函数遍历每个成员.

* 基本用法:

    ```JavaScript
    /*
    使用Set和forEach方法实现数组去重
    */

    //创建一个Set的实例s
    const s = new Set();

    //使用forEach遍历数组, 使用add()添加到s里
    [2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x));

    //输出s里的成员变量
    for (let i of s) {
      console.log(i);
    }
    // 2 3 5 4
    ```
    ​


#### Map

> Map类似于对象,是键值对的集合, 但是“键”的范围不限于字符串, 各种类型的值（包括对象）都可以当作键.
>
> Map是一个构造函数,可以创建Map数据结构.
>
> Map实例的操作数据的方法: add(value), delete(value), set(value), get(value)
>
> Map实例的遍历方法之一: `forEach()` 



* 基本用法:

  ```JavaScript
  var map = new Map([ ["name", "张三"], ["title", "Author"]]);

  map.size // 2
  map.has("name") // true
  map.get("name") // "张三"
  map.has("title") // true
  map.get("title") // "Author"
  ```

* 代码演示(2)

  ​

### 6.  Arrow function 箭头函数

> * 使用 “ 箭头 ”（`=>`）定义函数.
*  箭头函数不绑定自己的this, arguments, super.
*  箭头函数是匿名函数.
*  不能用作构造函数.


* 基本语法: 

  ```JavaScript
  // 无参数的函数需要使用圆括号
  () => { statements }

  //等同于
  function() { statements }
  ```



* 箭头函数 VS 普通函数

  ```JavaScript
  //ES6两种写法
  (i) => i + 1
  i => i + 1

  //ES5
  function(i) {
    return i + 1;
  }
  ```

* 有参数和无参数的写法

  ```JavaScript
  var f = () => 5;
  // 等同于
  var f = function () { return 5 };

  var sum = (num1, num2) => num1 + num2;
  // 等同于
  var sum = function(num1, num2) {
    return num1 + num2;
  };
  ```

* 简化回调函数

  ```JavaScript
  //普通函数写法
  [1, 2, 3].map(function (x) {
    return x * x;
  });

  //箭头函数写法
  [1, 2, 3].map(x => x * x);
  ```

* 代码演示(3)

   ​


### 7.  对象扩展方法

* 属性的简洁表达式

  ```JavaScript
  //直接写入属性
  var foo = 'bar';
  var obj = {foo};

  //等同于
  var obj = {foo: foo};

  //属性简写
  function f(x, y) {
    return {x, y};
  }
  //等同于
  functionf(x, y) {
    return {x:x, y:y };
  }
  ```


### 8.  Promise对象

> * Promise是一个对象，用来传递异步操作的消息
> * 异步操作的三种状态： 
>   Pending（进行中）
>   Resolved（已完成）
>   Rejected（已失败）
> * 同步/异步操作: 案例说明
> * 应用场景: Ajax

* 基本用法:

  ```JavaScript
  //创建一个Promise对象的实例,
  //两个参数都是函数, 分别是resolove和reject

  var promise = new Promise(function(resolve, reject) {
    // 执行一些操作
    
    if (/* 异步操作成功 */){
      resolve(value);
    } else {
      reject(error); 
    }
  });
  ```

* 代码演示(1)
```javascript
//应用场景： 回调函数嵌套“金字塔问题”
step1(function (value1) {
    step2(value1, function(value2) {
        step3(value2, function(value3) {
            step4(value3, function(value4) {
                // Do something with value4
            });
        });
    });
});

//使用promise
Q.fcall(promisedStep1)
.then(promisedStep2)
.then(promisedStep3)
.then(promisedStep4)
.then(function (value4) {
    // Do something with value4
})
.catch(function (error) {
    // Handle any error from all above steps
})
.done();


```
* promise的优势
1. 可以使用return和throw 堆栈
2. pollyfill

---

### 9.  对象继承`Class`和 `extends`

> 通过class关键字, 可以定义类, 实现类的继承。

* 基本用法

  ```JavaScript
  //ES6使用class定义类
  class Point {
    //必须使用consructor构造方法
    constructor(x, y) {
      this.x = x;
      this.y = y;
    }
    toString() {
      return '('+this.x+', '+this.y+')';
    }
  }

  //在ES5中使用原型(prototype)定义类
  function Point(x,y){
    this.x = x;
    this.y = y;
  }

  Point.prototype.toString = function () {
    return '('+this.x+', '+this.y+')';
  }
  ```

  ​



### 10. `Module`模块
>* 模块功能主要由两个命令构成：export和import。
* export命令用于规定模块的对外接口。
* import命令用于输入其他模块提供的功能。

* export基本用法
```javascript
// profile.js

// export关键词可以使外部读取内部的变量
export var firstName = 'Michael';
export var lastName = 'Jackson';
export var year = 1958;

//另一种写法
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export {firstName, lastName, year};

```

* import基本用法
```javascript
// main.js

// import命令可以加载export命令定义的对外接口
import {firstName, lastName, year} from './profile';

function setName(element) {
  element.textContent = firstName + ' ' + lastName;
}
```


* export default命令

输出一个匿名函数
```javascript
// export-default.js
export default function () {
  console.log('foo');
}
```

使用import为该匿名函数命名
```javascript
// import-default.js
import customName from './export-default';
customName(); // 'foo'
```

* 案例
1. 创建一个模块
  * 创建一个名为mortgage.js的文件.
  * 从main.js中复制calculateMonthlyPayment 函数和 calculateAmortization 函数.
  * 将`export`关键词放在变量声明的前方.


2. 使用这个模块
    *  在main.js里,移除这两个函数.
    *  将import放在main.js的第一行.
    ```javascrpit
    import * as mortgage from './mortgage';
    ```
    *  ​

3. Build 和 Run
    *  ​



## 四. ES6经典面试题分析

> 目前各大公司关于ES6相关面试题案例分析.

### 选择题 
*  以下代码会输出( )
```JavaScript
let name = 'zach'
while (true) {
    let name = 'obama'
    console.log(name)
    break
}
console.log(name) 
```

   a.  zach  zach

   b.  obama  obama

   c.  zach  obama

   d.  obama  zach

---

*   以下代码会输出( )

```JavaScript
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); 
```
   a.  10

   b. 1

   c.  6

   d.  0

---

* 以下代码会输出

   ```JavaScript
   var f = ([a, b] = [1, 2], {x: c} = {x: a + b}) => a + b + c;
   f();
   ```

   a.  2

   b.  5

   c.  6

   d.  3

---

### 填空题(5)


### 编程题(2)

1. 11
2. 11






## 五. 参考资源

### 1. 严格模式`'use strict';`
* 变量必须声明后再使用
* 函数的参数不能有同名属性，否则报错
* 不能使用with语句
* 不能对只读属性赋值，否则报错
* 不能使用前缀0表示八进制数，否则报错
* 不能删除不可删除的属性，否则报错
* 不能删除变量delete prop，会报错，只能删除属性delete global[prop]
* eval不会在它的外层作用域引入变量
* eval和arguments不能被重新赋值
* arguments不会自动反映函数参数的变化
* 不能使用arguments.callee
* 不能使用arguments.caller
* 禁止this指向全局对象
* 不能使用fn.caller和fn.arguments获取函数调用的堆栈
* 增加了保留字（比如protected、static和interface）


### 2. ES6新特性在Babel下的兼容性列表
| ES6特性   | 兼容性         |
| ------- | ----------- |
| 箭头函数    | 支持          |
| 类的声明和继承 | 部分支持，IE8不支持 |
|增强的对象字面量|	支持
|字符串模板	|支持
|解构|	支持，但注意使用方式
|参数默认值，不定参数，拓展参数|	支持
|let与const	|支持
|for of	|IE不支持
|iterator, generator|	不支持
|模块 module、Proxies、Symbol|	不支持
|Map，Set 和 WeakMap，WeakSet|	不支持
|Promises、Math，Number，String，Object 的新API	|不支持
|export & import|	支持
|生成器函数	|不支持
|数组拷贝|	支持


### 3. ES6资源
#### 文档
* [MDN ES6官网文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript) *最新,最全面的权威ES6指南*
* [Github ES6资源收集](https://github.com/ericdouglas/ES6-Learning)
* [ES6入门 阮一峰著](http://es6.ruanyifeng.com/) *语法, AIP速查手册,适合初学者入门*
* [ES6和ES5的比较 英语](http://es6-features.org/#SpreadOperator) *案例演示*
* [ES6的兼容和规范](http://imweb.io/topic/561f9352883ae3ed25e400f5)
* [ES6 tutorial](http://ccoenraets.github.io/es6-tutorial/)
  *ES6的最新案例实践*
* [ES6 案例](http://qnimate.com/post-series/ecmascript-6-complete-tutorial/) *基础案例*


####工具推荐: 
* [ES6在线转换](http://babeljs.cn/repl/) *在线测试ES6新特性*
* Chrom开发者插件`Scratch JS`   *ES6转换ES5,调试ES6代码*

