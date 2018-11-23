# 1. 简介



客户端API分为两类**

* 浏览器API
* 第三方API



**常见的浏览器API**

* 操作文档API
* 从服务器获取数据的API
* 用于绘制操作图形的API
* 音频和视频API
* 设备API
* 客户端存储API



**常见的第三方API**

- The [Twitter API](https://dev.twitter.com/overview/documentation), 允许您在您的网站上展示您最近的推文等。



### API 是如何工作的



共同的特性：

#### 它们是基于对象的

#### 具有可识别的入口

例如 稳定API 被挂载在 document 下。

#### 使用事件来处理状态的变化

#### 在适当的地方有额外的安全机制



# 2. 操作文档

Web浏览器的主要部分：

* window 是载入浏览器的标签。在JavaScript中用 Window 对象表示。
* navigator 标识浏览器存在于 web 上的状态和标识（即用户代理）。在 JavaScript 中，用Navigator 来表示。
* document 是载入窗口的实际页面，在 JavaScript 中，用 Document 对象表。



### 2.1 文档对象模型

在浏览器标签中当前载入的文档用文档对象模型来标识。这是一个由浏览器生成的"树结构"。

### 2.2 基本的DOM操作

```js
//查询
document.querySelector();
document.getElementById();
docuemnt.getElementByTagName();
//创建节点
document.createElement();
docuemnt.createTextNode();
//移动和删除节点
el.appendChild();
el.removeChild();
//操作样式
el.style.color="#000";
//操作属性
el.ssetAttributetyle('class','highlight')

```



### 2.3 从Window中获取有用的信息

例如从 window 中获取屏幕宽高， 监听屏幕大小变化。



# 3 从服务器获取数据

网页中用于处理HTTP请求的技术包括： XMLHttpRequest 、Fetch API

> 注： 在早期，这种通用技术被称为 Asynchronous JavaScript and XML（Ajax），因为它倾向于使用 XMLHttpRequest 来请求XML 数据。 但通常不是这种情况 (你更有可能使用 `XMLHttpRequest` 或 Fetch 来请求JSON), 但结果仍然是一样的，，但是术语“Ajax”仍然常用于描述这种技术。



### 3.1 基本的 Ajax 请求



####  XMLHttpRequest

20世纪90年代，由微软发明。跨浏览器兼容性优越。

```js
var request = new XMLHttpRequest();
request.open('GET', url);
request.responseType = 'text';
request.onload = function() {
  poemDisplay.textContent = request.response;
};
request.send();
```

#### Fetch

Fetch API 基本上是XHR的一个现代替代品，它是最近在浏览器中引入的，它使4异步HTTP请求JavaScript中更容易实现。

```js
fetch(url).then(function(response) {
  response.text().then(function(text) {
    poemDisplay.textContent = text;
  });
});
```

**fetch是基于原生的XMLHttpRequest对象来实现数据请求的。**

**同时，fetch也是基于Promise实现链式调用的。**

**那么，实现fetch的本质：就是实现ajax的封装以及Promise的实现。**



# 4 绘图

浏览器包含的图形编程工具，包括可缩放矢量图形（SVG）以及后来的 HTML 上的 canvas 元素上绘制图形的API。

本章讲解 canvas 的用法。

### 4.1 网络图形

canvas 用于改善和增加web对图形的支持 。用于提供更友好的动画，支持（CSS和SVG 不能支持更友好的动画，和位图。),canvas 提供了很多有用的工具，特别是当捆绑了由网络平台提供的API时，，用他们来生成2D动画，游戏画面和数据分析 ，以及其他类型的APP。



### 4.2 开始使用 canvas



要在网页中创建一个 2D 或者 3D 场景，必须要在HTML中插入一个 canvas 元素，以界定网页中的绘图区域。

```html
<canvas width="320" height="240"></canvas>
```

网页中会生成一块 320 * 320 像素的画布。

canvas 中一样可以放一些反馈信息：

```html
<canvas width="320" height="240">
  <p>卧槽你的浏览器竟然不支持 canvas！</p>
</canvas>
```



#### 创建画布，并确定尺寸



```js
var canvas = document.querySelector('.myCanvas');
var width = canvas.width = window.innerWidth;
var height = canvas.height = window.innerHeight;
```



####  获取画布上下文（canvas context），并完成设置。



创建一个 2d 画布：

```js
var ctx = canvas.getContext('2d');
```

ctx 变量 包含一个  [`CanvasRenderingContext2D`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D) 对象，画布上所有绘画操作都会涉及到这个对象。

> 可选上下文还包括 WebGL（webgl）、WebGL2（webgl2）等等。



将画布填充为黑丝

```js
ctx.fillStyle = 'rgb(0, 0, 0)';
ctx.fillRect(0, 0, width, height);
```



### 4.3 2D画布基础

画布中 左上角的坐标是（0,0），横坐标（x）轴向由延伸，纵坐标（y）轴向下延伸。



绘图操作可以基于原始的矩形模型实现，也可以通过追踪一个特定路径后填充颜色实现。

#### 简单矩形

```js
ctx.fillStyle = 'rgb(255, 0, 0)';
ctx.fillRect(50, 50, 100, 150);
//指定透明度
ctx.fillStyle = 'rgba(255, 0, 255, 0.75)';
ctx.fillRect(25, 100, 175, 50);
```



#### 描边和线条宽度



也可以不填充矩形，而对矩形进行描边绘制。

```js
ctx.strokeStyle = 'rgb(255, 255, 255)';
ctx.strokeRect(25, 25, 175, 200);
ctx.lineWidth = 5;
```



#### 绘制路径

可以通过绘制路径来绘制比矩形更复杂的图形。。画布提供了许多函数用来绘制直线、圆、贝塞尔曲线，等等。

主要API如下：

- [`beginPath()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/beginPath)：在钢笔当前所在位置开始绘制一条路径。在新的画布中，钢笔起始位置为 (0, 0)。
- [`moveTo()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/moveTo)：将钢笔移动至另一个坐标点，不记录、不留痕迹，只将钢笔“跳”至新位置。
- [`fill()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/fill)：通过为当前所绘制路径的区域填充颜色来绘制一个新的填充形状。
- [`stroke()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/stroke)：通过为当前绘制路径的区域描边，来绘制一个只有边框的形状。
- 路径也可和矩形一样使用 `lineWidth` 和 `fillStyle` / `strokeStyle` 等功能。

```js
ctx.fillStyle = 'rgb(255, 0, 0)';
ctx.beginPath();
ctx.moveTo(50, 50);
// 绘制路径
ctx.fill();
```

#### 绘制文本

以下两个函数用于绘制文本：

- [`fillText()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/fillText) ：绘制有填充色的文本。
- [`strokeText()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/strokeText)：绘制文本外边框（描边）。



#### 绘制图片

使用 drawImage 绘制图片

```js
var image = new Image();
image.src = 'firefox.png';

image.onload = function() {
  ctx.drawImage(image, 50, 50);
  //或者
  ctx.drawImage(image, 20, 20, 185, 175, 50, 50, 185, 175);
}

```

- 第一个参数不变，为图片引用。
- 参数 2、3 表示裁切部分左上顶点的坐标，参考原点为原图片本身左上角的坐标。原图片在该坐标左、上的部分均不会绘制出来。
- 参数 4、5 表示裁切部分的长、宽。
- 参数 6、7 表示裁切部分左上顶点在画布中的位置坐标，参考原点为画布左上顶点。
- 参数 8、9 表示裁切部分在画布中绘制的长、宽。本例中绘制时与裁切时面积相同，你也可以定制绘制的尺寸。





#### 循环和动画



### 4.4 WebGL



3D 画布内容可通过的 [WebGL](https://developer.mozilla.org/en-US/docs/Learn/WebGL) API 实现，尽管它和 2D canvas API 都可在 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/canvas) 元素上进行渲染，但两者是彼此独立的。



WebGL 基于 [OpenGL](https://developer.mozilla.org/en-US/docs/Glossary/OpenGL) 图形编程语言实现，可直接与 [GPU](https://developer.mozilla.org/en-US/docs/Glossary/GPU) 通信，基于此，编写纯 WebGL 代码与常规的 JavaScript 不尽相同，更像 C++ 那样的底层语言，更加复杂，但无比强大。



# 5 客户端存储



现代浏览器有着多种数据持久化方案，包括服务端存储，客户端存储。

客户端存储通常存在数据量的限制。通常的限制为 5M 到 10M 之间。



### 5.1 客户端存储



#### 5.1.1 老式的数据存储方案： Cookie

Cookies 从JavaScript 出现之初就一直存在，但是由于历史久远，cookie 也一直有这技术和体验方面的问题。

由于这些原因，后来 web 提出了更为安全和便捷的存储方式。

不过Cookie 依然是当你需要适配 IE 8 一下的浏览器时的客户端存储解决方案，因为新的API不支持IE 8 和更早的浏览器。



#### 5.1.2 新的方案： Web Storage 和 IndexedDB

* Web Storage APPI 提供了用于存储简单键值对数据的存储方案。
* IndexedDb API ，用于存储复杂的数据。 例如音频和视频文件。



#### 5.1.3 未来的存储方案： Cache API



一些现代浏览器，已经开始支持 Cache API，此API用于存储对特定请求的HTTP响应，对于执行诸如脱机存储网站资产之类的操作非常有用，因此可以在没有网络连接的情况下使用该站点。

### 5.2 存储简单数据： WebStorage 

WebStorage 包含两个对象： sessionStorage 和 localStorage。sessionStorage 存储的数据在浏览器标签打开期间有效。localStorage 存储的数据会一直有效。

这两个对象具有相同的数据存取方法：

```js
localStorage.setItem('name','Chris');
var myName = localStorage.getItem('name');
```



#### 不同的域下的 storage 是分离的



### 5.3 复杂数据的存储方案： IndexDB

IndexDB 是一个完整的数据库系统。可以用于存储图像，视频，和其他任何内容。



简单的用法如下：



打开一个已经创建的数据库，在onsuccess 中就可以操作数据库进行修改了

```js

let db;
let request = window.indexedDB.open('notes', 1);
// onerror handler signifies that the database didn't open successfully
request.onerror = function() {
  console.log('Database failed to open');
};

// onsuccess handler signifies that the database opened successfully
request.onsuccess = function() {
  console.log('Database opened successfully');

  // Store the opened database object in the db variable. This is used a lot below
  db = request.result;

  // Run the displayData() function to display the notes already in the IDB
  displayData();
};



```



当数据库还未被初始化时，需要在如下函数中进行初始化操作

```js
request.onupgradeneeded = function(e) {
  // Grab a reference to the opened database
  let db = e.target.result;

  // Create an objectStore to store our notes in (basically like a single table)
  // including a auto-incrementing key
  let objectStore = db.createObjectStore('notes', { keyPath: 'id', autoIncrement:true });

  // Define what data items the objectStore will contain
  objectStore.createIndex('title', 'title', { unique: false });
  objectStore.createIndex('body', 'body', { unique: false });

  console.log('Database setup complete');
};
```



添加一条数据：每一次的添加，实际上也是一个连接， 结果以回调方式返回。

```js
// grab the values entered into the form fields and store them in an object ready for being inserted into the DB
  let newItem = { title: titleInput.value, body: bodyInput.value };

  // open a read/write db transaction, ready for adding the data
  let transaction = db.transaction(['notes'], 'readwrite');

  // call an object store that's already been added to the database
  let objectStore = transaction.objectStore('notes');

  // Make a request to add our newItem object to the object store
  var request = objectStore.add(newItem);
  request.onsuccess = function() {
    // Clear the form, ready for adding the next entry
    titleInput.value = '';
    bodyInput.value = '';
  };

  // Report on the success of the transaction completing, when everything is done
  transaction.oncomplete = function() {
    console.log('Transaction completed: database modification finished.');

    // update the display of data to show the newly added item, by running displayData() again.
    displayData();
  };

  transaction.onerror = function() {
    console.log('Transaction not opened due to error');
  };
```

查询， 删除。



### 5.4 Offine asset storage

web  Storage 可以用于存储用户数据，但是却不能用于缓存 css html 和 js 文件。



Service worders 和 Cache API 用于解决这个问题，

* ServiceWorker，简单而言就是一个放在前端的 HTTP 拦截器，比如我们要请求一个不存在的 URI 如：`/test/a.html`，直接请求就会响应 404，而如果我们预先在 ServiceWorker 中注册了这个地址，并且指定响应内容，当再次请求时，你会看到结果是存在的，举个例子：

```js
navigator.serviceWorker.register("worker.js", {
  scope: ”/test/a.html"
}).then(function(){
  fetch(‘/test/a.html’).then(function(response) {
    return response.text();
  }).then(function(text) {
    console.log(text); 
  });
});
```

```js
// workker.js
addEventListener("fetch", function(evt) {
  evt.respondWith(new Response(“Hi, Barret Lee”));
});
```

* Cache API，简而言之就是一个 Request/Response 的缓存对象组，它的生命周期跟 ServiceWorker 是紧密相连的，它没有失效时间，不删除就会一直保持原样。



```
caches.open('test-cache').then(function(cache) {
  cache.add('/index.html');
});

caches.open('test-cache').then(function(cache) { 
  cache.keys().then(function(cachedRequests) { 
    console.log(cachedRequests);
  });
});


```



