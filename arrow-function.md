# 箭头函数 arrow function



![](http://i1.piimg.com/567571/f27f2fa148c205c5.png)



## 箭头函数   VS   普通函数


---

#### 箭头函数的优势

* 简洁的语法

![](http://i2.muimg.com/567571/85e209ce9173bfdd.png)

箭头函数

```JavaScript
let add = (a, b) => a + b
```



普通函数

```aJavaScript
let add = function(a, b) {
  return a + b;
}
```

---

* 语法

```JavaScript
    () => { ... } // no parameter
    
     x => { ... } // one parameter
     
(x, y) => { ... } // several parameters
```



* 函数体内表达式

```JavaScript
x => x * x  // expression

// 等同于
x => { return x * x } 
```

```JavaScript
// ES6 箭头函数
const squares = [1, 2, 3].map(x => x * x);

// 普通函数
const squares = [1, 2, 3].map(function (x) { return x * x });
```







* 没有this绑定

  that = this

```JavaScript
function Prefixer(prefix) {
    this.prefix = prefix;
}
Prefixer.prototype.prefixArray = function (arr) {
    var that = this; // (A)
    return arr.map(function (x) {
        return that.prefix + x;
    });
};

> var pre = new Prefixer('Hi ');
> pre.prefixArray(['Joe', 'Alex'])
[ 'Hi Joe', 'Hi Alex' ]
```



