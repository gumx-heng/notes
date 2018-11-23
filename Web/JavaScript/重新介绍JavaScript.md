JS 教程 语法概念重新整理

JS没有输入和输出的概念，它是一个在主机环境（host environment）下运行的脚本语言，任何与外界沟通的机制都是由主机环境提供的。浏览器是最常见的主机环境，但在非常多的其他程序中也包含 JavaScript 解释器，如 Adobe Acrobat、Photoshop、SVG 图像、Yahoo! 的 Widget 引擎，以及 Node.js 之类的服务器端环境。实际应用远不止如这些。



### 概览



JavaScript 是一种面向对象的动态语言，它包含类型，运算符、标准内置对象和方法。



类型如下：

- Number（数字）
- [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)（字符串）
- [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Boolean)（布尔）
- [`Symbol`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)（符号）（第六版新增）
- Object（对象）
  - [`Function`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Function)（函数）
  - [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)（数组）
  - [`Date`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Date)（日期）
  - [`RegExp`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/RegExp)（正则表达式）
- [`Null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Null)（空）
- Undefined（未定义）



### 数字

JavaScript 采用“IEEE 754 标准定义的双精度64位格式”（"double-precision 64-bit format IEEE 754 values"）表示数字。所以JavaScript不区分整数值和浮点数值，所有JavaScript中均用浮点数值标识。

```js
0.1 + 0.2 = 0.30000000000000004//问题
```



#### JavaScript支持标准的算术运算符，以及内置对象Math（数学对象）。

```js
Math.sin(3.5);
var d = Math.PI * (r + r);
```



#### 关于 NaN

如果给定的字符串不存在数值形式，函数会返回一个特殊的值 [`NaN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/NaN)（Not a Number 的缩写）。

如果把 `NaN` 作为参数进行任何数学运算，结果也会是 `NaN`。

#### 两个特殊值 Infinity（正无穷）和 -Infinity（负无穷）



### 字符串



JavaScript 中的字符串是一串 Unicode字符序列。



### 其他类型

JavaScript 中 null 和 undefined 是不同的，前者表示一个空值（non-value），必须使用null关键字才能访问，后者是“undefined（未定义）”类型的对象，表示一个未初始化的值，也就是还没有被分配的值。

JavaScript 包含布尔类型，这个类型的变量有两个可能的值，分别是 `true` 和 `false`（两者都是关键字）。根据具体需要，JavaScript 按照如下规则将变量转换成布尔类型：

1. `false`、`0`、空字符串(`""`)、`NaN`、`null` 和 `undefined` 被转换为 `false`
2. 所有其他值被转换为 `true`

JavaScript 支持包括 `&&`（逻辑与）、`||` （逻辑或）和`!`（逻辑非）在内的逻辑运算符。下面会有所提到。



### 变量

在 JavaScript 中声明一个新变量的方法是使用关键字 let 、const 和 var：

**let** 语句声明一个块级作用域的本地变量，并且可选的将其初始化为一个值。

**const** 允许声明一个不可变的常量。这个常量在定义域内总是可见的。

**var** 这是传统上在 JavaScript 声明变量的唯一方法。使用 **var** 声明的变量在它所声明的整个函数都是可见的。



传统的 JavaScript 是没有块作用域的，只有函数作用域。但是从ECMAScript Edition 6 开始，let 和 const 关键字所创建的变量其有效范围是块作用域，也就是 es6 之后才有了块作用域。

### 运算符

JavaScript的算术操作符包括 +、-、*、/ 和 % ——求余（与模运算不同）。赋值使用 = 运算符，此外还有一些复合运算符，如 += 和 -=，它们等价于 x = x op y。

JavaScript 中的比较操作使用 <、>、<= 和 >=，这些运算符对于数字和字符串都通用

JavaScript 还支持 != 和 !== 两种不等运算符，具体区别与两种相等运算符的区别类似。

JavaScript 还提供了 位操作符。

### 控制结构

* if else

* while do （do while）

* for （for of , for in）

* `&&` 和 `||` 运算符使用短路逻辑（short-circuit logic），是否会执行第二个语句（操作数）取决于第一个操作数的结果。在需要访问某个对象的属性时，使用这个特性可以事先检测该对象是否为空：

  ```js
  var name = o && o.getName();
  var name = otherName || "default";
  ```

* swith

### 对象

JavaScript 中的对象可以简单理解成“名称-值”对。 类似于 java里 HashMap

创建对象有一下两种简单的方法：

```js
var obj = new Object();
var obj = {};
```

这两种方法在语义上是相同的。第二种更方便的方法叫作“对象字面量（object literal）”法。这种也是 JSON 格式的核心语法，一般我们优先选择第二种方法。

#### 读取对象属性

链式访问和方括号访问

```js
obj.name = "Simon"
obj['name'] = 'Simon';

var name = obj.name;
var name = obj['name'];
```

这两种方法在语义上是相同的。第二种方法的有点在于属性的名称是 被看做一个字符串的，这就意味着它可以在运行时被计算，缺点在于这样的代码有可能在后期无法被解释器优化。它可以被用来访问某些以预留关键字作为名称的属性的值：

```js
obj.for = "Simon"; // 语法错误，因为 for 是一个预留关键字
obj["for"] = "Simon"; // 工作正常
```



### 数组

#### 创建数组的几种方式：

* 传统方式：

```js
var a = new Array();
a[0] = "dog";
a[1] = "cat";
a[2] = "hen";
a.length; // 3
```

* 字面量方式

```js
var a = ["dog", "cat", "hen"];
a.length; // 3
```

#### 访问不存在的索引会返回 undefined

#### 遍历数组

* for in
* for of
* for in（实际上是遍历对象属性的方法）

### 函数 

```js
function add(x, y) {
    var total = x + y;
    return total;
}
```

所有的函数都是有返回值的，如果没有写return 会默认返回 undefined。



函数在访问参数的时候，十几场是访问了函数体中一个叫做 arguments 的内部对象，这个对象就如同一个类似于数组的对象一样，包括了所有被传入的参数。

```js
function add() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
        sum += arguments[i];
    }
    return sum;
}

add(2, 3, 4, 5); // 14
```

JavaScript 允许以递归方式调用函数。

```js
function countChars(elm) {
    if (elm.nodeType == 3) { // 文本节点
        return elm.nodeValue.length;
    }
    var count = 0;
    for (var i = 0, child; child = elm.childNodes[i]; i++) {
        count += countChars(child);
    }
    return count;
}
```

JavaScript 允许你命名匿名函数表达式。

```js
var charsInBody = (function counter(elm) {
        if (elm.nodeType == 3) { // 文本节点
        return elm.nodeValue.length;
    }
    var count = 0;
    for (var i = 0, child; child = elm.childNodes[i]; i++) {
        count += counter(child);
    }
    return count;
})(document.body);
```

### 自定义对象

```js
function makePerson(first, last) {
    return {
        first: first,
        last: last,
        fullName: function() {
            return this.first + ' ' + this.last;
        },
        fullNameReversed: function() {
            return this.last + ', ' + this.first;
        }
    }
}
s = makePerson("Simon", "Willison");
s.fullName(); // Simon Willison
s.fullNameReversed(); // Willison, Simon
```

**这里this需要注意的是：当使用在函数中时，`this` 指代当前的对象，也就是调用了函数的对象。**



另一个方式 new

```js
s = new Person("Simon", "Willison");
```

关于 apply



### 内部函数

JavaScript 允许在一个函数内部定义函数，

**关于 JavaScript 中的嵌套函数，一个很重要的细节是它们可以访问父函数作用域中的变量：**

```js
function betterExampleNeeded() {
    var a = 1;
    function oneMoreThanA() {
        return a + 1;
    }
    return oneMoreThanA();
}
```



### 闭包

 JavaScript 中必须提到的功能最强大的抽象概念之一：闭包。

```js
function makeAdder(a) {
    return function(b) {
        return a + b;
    }
}
var x = makeAdder(5);
var y = makeAdder(20);
x(6); // ?
y(7); // ?
```

这里发生的事情和前面介绍过的内嵌函数十分相似：一个函数被定义在了另外一个函数的内部，内部函数可以访问外部函数的变量。唯一的不同是，外部函数已经返回了，那么常识告诉我们局部变量“应该”不再存在。但是它们却仍然存在——否则 `adder` 函数将不能工作。也就是说，这里存在 `makeAdder` 的局部变量的两个不同的“副本”——一个是 `a` 等于5，另一个是 `a` 等于20。那些函数的运行结果就如下所示：

```js
x(6); // 返回 11
y(7); // 返回 27
```



下面来说说到底发生了什么。每当 JavaScript 执行一个函数时，都会创建一个作用域对象（scope object），用来保存在这个函数中创建的局部变量。它和被传入函数的变量一起被初始化。这与那些保存的所有全局变量和函数的全局对象（global object）类似，但仍有一些很重要的区别，第一，每次函数被执行的时候，就会创建一个新的，特定的作用域对象；第二，与全局对象（在浏览器里面是当做 `window` 对象来访问的）不同的是，你不能从 JavaScript 代码中直接访问作用域对象，也没有可以遍历当前的作用域对象里面属性的方法。



所以当调用 `makeAdder` 时，解释器创建了一个作用域对象，它带有一个属性：`a`，这个属性被当作参数传入 `makeAdder` 函数。然后 `makeAdder` 返回一个新创建的函数。通常 JavaScript 的垃圾回收器会在这时回收 `makeAdder` 创建的作用域对象，但是返回的函数却保留一个指向那个作用域对象的引用。结果是这个作用域对象不会被垃圾回收器回收，直到指向 `makeAdder` 返回的那个函数对象的引用计数为零。

作用域对象组成了一个名为作用域链（scope chain）的链。它类似于原型（prototype）链一样，被 JavaScript 的对象系统使用。

一个**闭包**就是一个函数和被创建的函数中的作用域对象的组合。

闭包允许你保存状态——所以它们通常可以代替对象来使用。[这里](http://stackoverflow.com/questions/111102/how-do-javascript-closures-work)有一些关于闭包的详细介绍。





### 内存泄露

使用闭包的一个坏处是，在 IE 浏览器中它会很容易导致内存泄露。

JavaScript 是一种具有垃圾回收机制的语言——对象在被创建的时候分配内存，然后当指向这个对象的引用计数为零时，浏览器会回收内存。

IE 浏览器有自己的一套垃圾回收机制，这套机制与 JavaScript 提供的垃圾回收机制进行交互时，可能会发生内存泄露。

在 IE 中，每当在一个 JavaScript 对象和一个本地对象之间形成循环引用时，就会发生内存泄露。如下所示：

```html
function leakMemory() {
    var el = document.getElementById('el');
    var o = { 'el': el };
    el.o = o;
}
```

这段代码的循环引用会导致内存泄露：IE 不会释放被 `el` 和 `o` 使用的内存，直到浏览器被彻底关闭并重启后。

闭包很容易发生无意识的内存泄露。如下所示：

```html
function addHandler() {
    var el = document.getElementById('el');
    el.onclick = function() {
        el.style.backgroundColor = 'red';
    }
}
```



这个问题有很多种解决方法，最简单的一种是不要使用 `el` 变量：

```html
function addHandler(){
    document.getElementById('el').onclick = function(){
        this.style.backgroundColor = 'red';
    };
}
```

另外一种避免闭包的好方法是在 `window.onunload` 事件发生期间破坏循环引用。很多事件库都能完成这项工作。注意这样做将使 [Firefox 中的 bfcache](https://developer.mozilla.org/en-US/docs/Using_Firefox_1.5_caching) 无法工作。所以除非有其他必要的原因，最好不要在 Firefox 中注册一个`onunload` 的监听器。

