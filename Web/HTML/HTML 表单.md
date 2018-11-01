## 1. 您的第一个 HTML 表单



### 1.1 设计表单



一个完整的 HTML 表单由一个 from（容器） 元素包含一些 input 或者 textarea （输入元素）元素，和 button 按钮。





#### from 元素

所有 HTML 元素都是已一个 from 元素开始的：

```html
<form action="/my-handling-form-page" method="post">

</form>
```



* action 属性定义了提交的目的 URL。
* method 属性定义了发送数据的 HTTP 方法（get 或者 post）。



#### label，input 和 textarea 元素

在label 元素上使用 for 属性，将 label 标签链接到其他表单小部件。

input 元素和 textarea 元素，用于存储表单值。



#### button 元素

```html
<div class="button">
<button type="submit">Send your message</button>
</div>
```

button 元素的 type 属性很重要，它接受三个值 submit、reset、button，分别表示不同的作用：

* submit ： 点击此按钮，将会发送数据到 from 元素的 action所定义的 URL。
* reset ： 点击此按钮，会将将所有表单部件的值设置为他们的默认值。
* button： 点击此按钮，不会发生任何表单时间。但是可以用 JavaScript 定制事件。



## 2.  如何构建 HTML 表单

在构建 HTML 表单 时使用正确的结构将有助于确保表单可用性和可访问性。



### 2.1 form 元素



form 按照一定的格式定义了表单和确定表单行为的属性。当创建表单时必须以这个元素开始，其他内容都要放在里面。



### 2.2 fieldset 和 legend 元素



fieldset 和 legend 元素用于创建具有相同目的的**小部件==组==**。用例如下：



```html
form>
  <fieldset>
    <legend>Fruit juice size</legend>
    <p>
      <input type="radio" name="size" id="size_1" value="small">
      <label for="size_1">Small</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_2" value="medium">
      <label for="size_2">Medium</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_3" value="large">
      <label for="size_3">Large</label>
    </p>
  </fieldset>
</form>
```



效果如下：

![1539660493841](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_1.png)





### 2.3 label 元素



label 元素是为HTML表单小部件定义标签的正式方法。

```html
<label for="name">Name:</label> <input type="text" id="name" name="user_name">
```



#### 标签也可以点击



正确的设置标签的另一个好处就是可以在所有浏览器这个点击标签来激活相应的小部件，特别是对单选框和复选框很有效。



#### 多个标签

当有一个小部件内包含多个标签的时候，最好的写法应该是这样的：

```html
<div>
  <label for="username">Name: <abbr title="required">*</abbr></label>
  <input id="username" type="text" name="username">
</div>
```



### 2.4 用于表单的通用 HTML 结构

除了HTML 表单结构之外，你也可以使用其他元素来构建更为强大的HTML表单。

比如：也可以用div或者p标签包括小部件组，除了fiedset元素外，也可以使用 h1 h2等元素设置表单标题，也可以使用 section 元素进行分段。

下面是一个完整的例子：

```html
<form action="#"> 
    <section>
        <h2>Contact information</h2>
        <fieldset>
          <legend>Title</legend>
          <ul>
              <li>
                <label for="title_1">
                  <input type="radio" id="title_1" name="title" value="M." >
                  Mister
                </label>
              </li>
              <li>
                <label for="title_2">
                  <input type="radio" id="title_2" name="title" value="Ms.">
                  Miss
                </label>
              </li>
          </ul>
        </fieldset>
        <p>
          <label for="name">
            <span>Name: </span>
            <strong><abbr title="required">*</abbr></strong>
          </label>
          <input type="text" id="name" name="username">
        </p>
        <p>
          <label for="mail">
            <span>E-mail: </span>
            <strong><abbr title="required">*</abbr></strong>
          </label>
          <input type="email" id="mail" name="usermail">
        </p>
        <p>
          <label for="pwd">
            <span>Password: </span>
            <strong><abbr title="required">*</abbr></strong>
          </label>
          <input type="password" id="pwd" name="password">
        </p>
    </section>
    <section>
        <h2>Payment information</h2>
        <p>
          <label for="card">
            <span>Card type:</span>
          </label>
          <select id="card" name="usercard">
            <option value="visa">Visa</option>
            <option value="mc">Mastercard</option>
            <option value="amex">American Express</option>
          </select>
        </p>
        <p>
          <label for="number">
            <span>Card number:</span>
            <strong><abbr title="required">*</abbr></strong>
          </label>
            <input type="text" id="number" name="cardnumber">
        </p>
        <p>
          <label for="date">
            <span>Expiration date:</span>
            <strong><abbr title="required">*</abbr></strong>
            <em>formatted as mm/yy</em>
          </label>
          <input type="text" id="date" name="expiration">
        </p>
    </section>
    <p> <button type="submit">Validate the payment</button> </p>
</form>
```



![1539665213345](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_2.png)





## 3. 原生表单挂件



涵盖了所有可用的原生表单小部件。



### 3.1 通用属性：

* autofocus  默认false  自动具有输入焦点
* disabled  默认false  如果没有指定这个属性，元素将从包含的元素集成它的设置
* form  小部件与之相关联的表单元素，都不支持，没啥用。
* name  元素的名称，用于表单数据的提交
* value 元素的初始值。



### 3.2 文本输入域

文本输入域 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input) 是最基本的表单小部件。

所有的文本域都有一些通用规范：

* 都可以被标记为readonly（只读）或者disabled（输入的值将不会被表单发送）
* 都可以有一个placehoder
* 都可以设置尺寸样式
* 如果浏览器支持，可以从检查拼写中获益。



#### 单行文本域 （type=text）

```html
<input type="text" id="comment" name="comment" value="I'm a text field">
```

单行文本域只有一个真正的约束：如果您输入带有换行符的文本，浏览器会在发送数据之前删除这些换行符。



#### E-mail 地址域 （type=email）

此时用户需要在域中输入有效的电子邮件地址；任何其他内容都会导致浏览器在提交表单时显示错误。注意，这是客户端错误验证，由浏览器执行：



![1539668733502](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_3.png)



通过包括 multiple 属性，可以让用户将多个电子邮件地址输入相同的输入（以逗号分隔）。

#### 密码域 （type=password）

它不会为输入的文本添加任何特殊的约束，但是它会模糊输入到字段中的值。



#### 搜索域 （type=search）

通常，搜索字段以圆角和/或给定一个“x”来清除输入的值。

另外一个值得注意的特性:它们的值可以自动保存到同一站点上的多个页面上自动完成。



#### 电话号码域 （type=tel）

这种类型的字段不会对用户输入的值执行任何限制

这主要是语义上的差异，尽管在一些设备上(特别是在移动设备上)，可能会出现一个不同的虚拟键盘，更适合输入电话号码。



#### URL 域 （type=url）

它为字段添加了特殊的验证约束，如果输入无效的url，浏览器就会报告错误。



#### 多行文本域 （textarea）

```html
<textarea cols="30" rows="10"></textarea>
```

**元素属性：**

* cols  （默认值20） 文本控件的可见宽度，平均字符宽度。
* rows  控制的可见文本行数。
* wrap  默认值（soft）表示空间是如何包装文本的，可选值有： hard 和 soft



**注： texteara 元素是一个常规元素，可以包含文本内容的子元素（默认值）**



### 3.3 下拉内容



HTML有两种类型的下拉内容：select box 和 autocomplete box。



#### 选择框 select

select元素用于创建选择框，option作为子选项。可以通过multiple指定是否多选。

可以使用 optgroup 元素对option进行分组。

```html
<select id="groups" name="groups">
  <optgroup label="fruits">
    <option>Banana</option>
    <option selected>Cherry</option>
    <option>Lemon</option>
  </optgroup>
  <optgroup label="vegetables">
    <option>Carrot</option>
    <option>Eggplant</option>
    <option>Potato</option>
  </optgroup>
</select>
```



如果option有value属性，则采用value的值，如果没有则采用option标签中的字段。



#### 自动补全输入框 dataalist

可以使用datalist元素来为表单小部件提供建议的，自动完成的值，用例如下：

```html
<label for="myFruit">What's your favorite fruit?</label>
<input type="text" name="myFruit" id="myFruit" list="mySuggestion">
<datalist id="mySuggestion">
  <option>Apple</option>
  <option>Banana</option>
  <option>Blackberry</option>
  <option>Blueberry</option>
  <option>Lemon</option>
  <option>Lychee</option>
  <option>Peach</option>
  <option>Pear</option>
</datalist>
```



![1539669508965](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_4.png)

**注：由于datalist元素是HTML表单的最新补充，因此浏览器的支持还很少。IE10一下，Safair都不支持**





### 3.4 可选中项



复选框和单选按钮。

```html
<-- 复选 !-->
<input type="checkbox" checked id="carrots" name="carrots" value="carrots"> 
<-- 单选 !-->
<input type="radio" checked id="soup" name="meal">
```

当name一致时，将被视为一组按钮。



### 3.5 按钮 button



HTML表单中有三种按钮：submit、reset、button。通过type设定。

```html
<button type="submit">
    This a <br><strong>submit button</strong>
</button>
```



### 3.6 高级表单部件



#### 数字 （type=number）

用于数字的小部件是用input元素创建的，它的`type`属性设置为`number`。

只允许浮点数，并且通常提供一些按钮来增加或减少小部件的值。

**元素属性**

* min 和 max 设置约束值。
* step 设置按钮触发的改动值。

```html
<input type="number" name="age" id="age" min="1" max="10" step="2">
```

效果如下：

![1539670077683](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_5.png)

#### 滑块 （type=range）

input 元素type设置为range，一样拥有min、max、step属性

```html
<input type="range" name="beans" id="beans" min="0" max="500" step="10">
```

效果如下：

![1539670225942](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_6.png)



#### 日期选择器 （type=time）

input元素，指定type=time。通过name指定选月或者周，基本没啥用，因为太丑。。。

chrome下如下图：

![1539670543978](F:\Nextcloud Data\Git Repositories\notes\Web\HTML\images\HTML 表单_7.png)





#### 拾色器 （type=color）

IE中没有支持，Safari目前也不支持它。其他主要的浏览器都支持它。



### 3.7 其他小部件



#### 文件选择器 （type=file）

使用input元素，指定type=file，并通过accept属性来约束文件类型，同时也可以通过指定mutiple属性来选择多个文件。

```html
<input type="file" name="file" id="file" accept="image/*" multiple>
```

#### 图像按钮 （type=img）



使用 input 元素，指定type=img，可以创建图片类型的按钮。使用src属性指定图片url。

```html
<input type="image" alt="Click me!" src="my-img.png" width="80" height="30" />
```

如果使用图像按钮来提交表单，这个小部件不会提交它的值；相反，在图像上单击的X和Y坐标是被提交的(坐标是相对于图像的，这意味着图像的左上角表示坐标0，0)，坐标被发送为两个键/值对。



但是我试了下，用onclick 获取不到。



#### 3.8 仪表和进度条



##### 进度条

一个进度条表示一个值，它会随着时间的变化而变化到最大的值，这个值由`max`属性指定。这样的一个bar是使用[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress)元素创建的。



```html
<progress max="100" value="75">75/100</progress>
```

##### 仪表

用于表示当前值的进度，并通过颜色显示当前值的类型（优先、平均或者糟糕）。



```html
<meter min="0" max="100" value="75" low="33" high="66" optimum="50">75</meter>
```



## 4 发送表单数据

在这里，我们将讨论在提交表单时数据会发生什么。



###  4.1 客户端/服务器体系结构



web基于非常基础的客户端/服务器体系结构：客户端想服务器发送请求，使用HTTP协议。服务器使用相同的策略来回答请求。

### 4.2 在客户端：定义如何发送数据

form元素的 action和method属性是最重要的两个属性，定义了发送地址和发送方法（post、get）。

### 4.3 在服务端检：检索数据

无论选择哪种HTTP方法，服务器都会接收一个字符串并解析它以获取作为键/值对序列的数据。



### 4.4 特殊案例： 发送文件

用HTML表单发送文件是一个特殊的例子。文件是二进制数据----或者被认为是这样的----而所有其他数据都是文本书。由于HTTP是一种文本协议，所以处理二进制数据有特殊的要求。



#### enctype 属性



该属性用于指定提交表单时所生成的请求中的content-type的http数据头的值。这个值用于高速服务器正在发送生么样的数据。默认情况下，他的值是 application/x-www-form-urlencoded 。他的意思是：“这是已编码为URL参数的表单数据。”

如果要发送的是文件，需要额外的三个步骤：

* 将methods属性设置为 POST。
* 将enctype值设置为multipart/form-data。因为数据将被分成多个部分，每个文件分别对应一个问价以及表单正文中包含的文本数据。
* 包含一个或多个File picker 小部件，允许用于选择将要上传的文件。



```html
<form method="post" enctype="multipart/form-data">
  <div>
    <label for="file">Choose a file</label>
    <input type="file" id="file" name="myFile">
  </div>
  <div>
    <button>Send the file</button>
  </div>
</form>
```



### 4.5 最常见的安全问题

到目前为止，HTML表单是最常见的攻击媒介(可能发生攻击的地方)。这些问题从来都不是来自HTML表单本身，它们来自于服务器如何处理数据。



#### XSS 和 CSRF

跨站脚本(XSS)和跨站点请求伪造(CSRF)是常见的攻击类型，它们发生在当您将用户发送的数据显示给用户或另一个用户时。

首相两种攻击方式都是向Web页面中注入客户端脚本。但是他们的目标各不相同。

XSS攻击利用用户对web站点的信任，而CSRF攻击则利用网站为其用户提供的信任。



#### SQL注入

SQL 注入是一种试图在目标web站点使用的数据库上执行操作的攻击类型。这通常包括发送一个SQL请求，希望服务器能够执行它。



#### HTTP数据头注入和电子邮件注入

当您的应用程序基于表单上用户的数据输入构建HTTP头部或电子邮件时，就会出现这种类型的攻击。这些不会直接损害您的服务器或影响您的用户，但是它们是一个更深入的问题，例如会话劫持或网络钓鱼攻击。

这些攻击大多是无声的，并且可以将您的服务器变成[僵尸](http://en.wikipedia.org/wiki/Zombie_(computer_science))。



#### 解决方案：（服务端）永远不要相信你的用户



## 5 表单验证



### 5.1 使用内置表单数据验证



HTML5 的一个新功能就是，可以在不写一行代码的情况下实现对用户输入的数据校验。

当验证通过时input元素会被添加CSS伪类 :vaild ，当验证未通过时input元素会被添加CSS伪类 ：invalid。



#### require属性

require属性用于验证输入不能为空。

```html
<input id="choose" name="i_like" required>
```



#### 使用正则表达式验证

另一个常用的验证功能是 pattern 属性，已 Regular Expression 作为value值，

例如：

```html
<form>
  <label for="choose">Would you prefer a banana or a cherry?</label>
  <input id="choose" name="i_like" required pattern="banana|cherry">
  <button>Submit</button>
</form>
```

其中require属性验证不能为空，pattern验证输入内容的正则匹配规则。



#### 强制条目长度



使用 minlength 和 maxlength 来限制输入元素的长度。如下：

```html
<form>
  <div>
    <label for="choose">Would you prefer a banana or a cherry?</label>
    <input id="choose" name="i_like" required minlength="6" maxlength="6">
  </div>
    <button>Submit</button>
  </div>
</form>
```

#### 自定义错误信息



由于默认的错误提示太过简介，而且有时无法说明具体的错误信息，此时就可以通过自定义错误信息来实现了：

```html
<form>
  <label for="mail">I would like you to provide me an e-mail</label>
  <input type="email" id="mail" name="mail">
  <button>Submit</button>
</form>
```

对于上面的例子，可以调用如下js实现自定义错误信息：



```js
var email = document.getElementById("mail");

email.addEventListener("input", function (event) {
  if (email.validity.typeMismatch) {
    email.setCustomValidity("I expect an e-mail, darling!");
  } else {
    email.setCustomValidity("");
  }
});
```



### 5.2 使用 JavaScript 校验表单



HTML 5 提供了大量的表单验证的API，和两个检验约束API的方法，用这些API就足以实现表单的验证。



#### 用于校验的API及属性



比较多，就不列举了。 以validity为主。



#### 校验约束API的方法



* checkValidity()   如果元素的值不存在验证问题，返回 `true`，否则返回 `false`。如果元素验证失败，此方法会触发`invalid` 事件。

* setCustomValidity(*message*)    为元素添加一个自定义的错误消息；如果设置了自定义错误消息，则该元素被认为是无效的，并显示指定的错误。这允许你使用 JavaScript 代码来建立验证失败，而不是用标准约束验证 API 所提供的。在报告问题时，将向用户显示自定义消息。

  如果参数为空，则清空自定义错误  



#### 用例：

**HTML 部分：**



```html
<form novalidate>
  <p>
    <label for="mail">
      <span>Please enter an email address:</span>
      <input type="email" id="mail" name="mail">
      <span class="error" aria-live="polite"></span>
    </label>
  </p>
  <button>Submit</button>
</form>
```



[`aria-live`](https://developer.mozilla.org/en-US/docs/Accessibility/ARIA/ARIA_Live_Regions) 属性确保我们的自定义错误信息将呈现给所有人，包括使用屏幕阅读器等辅助技术的人。



**CSS 样式**

```css
/* 仅为了使示例更好看 */
body {
  font: 1em sans-serif;
  padding: 0;
  margin : 0;
}

form {
  max-width: 200px;
}

p * {
  display: block;
}

input[type=email]{
  -webkit-appearance: none;

  width: 100%;
  border: 1px solid #333;
  margin: 0;

  font-family: inherit;
  font-size: 90%;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* 验证失败的元素样式 */
input:invalid{
  border-color: #900;
  background-color: #FDD;
}

input:focus:invalid {
  outline: none;
}

/* 错误消息的样式 */
.error {
  width  : 100%;
  padding: 0;
 
  font-size: 80%;
  color: white;
  background-color: #900;
  border-radius: 0 0 5px 5px;
 
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.error.active {
  padding: 0.3em;
}
```





**JavaScript**

以下 JavaScript 代码演示如何处理自定义错误验证。

```js
// 有许多方式可以获取 DOM 节点；在此我们获取表单本身和
// email 输入框，以及我们将放置错误信息的 span 元素。

var form  = document.getElementsByTagName('form')[0];
var email = document.getElementById('mail');
var error = document.querySelector('.error');

email.addEventListener("input", function (event) {
  // 当用户输入信息时，验证 email 字段
  if (email.validity.valid) {
    // 如果验证通过，清除已显示的错误消息
    error.innerHTML = ""; // 重置消息的内容
    error.className = "error"; // 重置消息的显示状态
  }
}, false);
form.addEventListener("submit", function (event) {
  // 当用户提交表单时，验证 email 字段
  if (!email.validity.valid) {
    
    // 如果验证失败，显示一个自定义错误
    error.innerHTML = "I expect an e-mail, darling!";
    error.className = "error active";
    // 还需要阻止表单提交事件，以取消数据传送
    event.preventDefault();
  }
}, false);
```



### 5.3 不使用内建的 API验证



即普通的JS验证，获取输入，验证输入，回馈结果。



### 5.3 远程验证

即服务端验证





## 6 如何构建自定义表单挂件



关键在于： 设计、结构、和语义。



## 7 通过 JavaScript 发送表单

现代Web站点更多的是用表单来收集数据，然后用异步发送数据，而不再使用表单发送数据。



### 7.1 发送表单数据

一共有三种方式发送表单数据：这包括一种传统方式和一种利用 formData 对象的新方法。

### 

#### 在DOM中构建一个隐藏的iframe

异步发送表单数据的最古老方法是用DOM API构建表单，然后将其数据发送到隐藏的[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)。 要访问提交的结果，请获取[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe)的内容。



#### 手动创建XMLHttpRequiuest



[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)是进行HTTP请求的最安全和最可靠的方式。 要使用[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)发送表单数据，请通过对URL进行编码来准备数据，并遵守表单数据请求的具体内容。



用例：



```
function sendData(data) {
  var XHR = new XMLHttpRequest();
  var urlEncodedData = "";
  var urlEncodedDataPairs = [];
  var name;

  // 将数据对象转换为URL编码的键/值对数组。
  for(name in data) {
    urlEncodedDataPairs.push(encodeURIComponent(name) + '=' + encodeURIComponent(data[name]));
  }

  // 将配对合并为单个字符串，并将所有%-编码空间替换为
  // “+”字符；匹配浏览器窗体提交的行为。
  urlEncodedData = urlEncodedDataPairs.join('&').replace(/%20/g, '+');

  // 定义成功数据提交时发生的情况
  XHR.addEventListener('load', function(event) {
    alert('Yeah! Data sent and response loaded.');
  });

  // 定义错误提示
  XHR.addEventListener('error', function(event) {
    alert('哎呀！出了问题。');
  });

  // 建立我们的请求
  XHR.open('POST', 'https://example.com/cors.php');

  // 为表单数据POST请求添加所需的HTTP头
  XHR.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

  // 最后，发送我们的数据。
  XHR.send(urlEncodedData);
}
```





#### 使用 XMLHttpRequest 和 the FormData object （表单对象）



用例：



```js
function sendData(data) {
  var XHR = new XMLHttpRequest();
  var FD  = new FormData();

  // 把我们的数据添加到这个FormData对象中
  for(name in data) {
    FD.append(name, data[name]);
  }

  // 定义数据成功发送并返回后执行的操作
  XHR.addEventListener('load', function(event) {
    alert('Yeah! Data sent and response loaded.');
  });

  // 定义发生错误时执行的操作
  XHR.addEventListener('error', function(event) {
    alert('Oups! Something goes wrong.');
  });

  // 设置请求地址和方法
  XHR.open('POST', 'http://ucommbieber.unl.edu/CORS/cors.php');

  // 发送这个formData对象,HTTP请求头会自动设置
  XHR.send(FD);
}
```



##### 使用绑定到表单元素上的 FormData 



你也可以绑定一个 `FormData` 对象到一个 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form) 元素上。这会创建一个 `FormData` ，代表表单中包含的元素。



```html
<form id="myForm">
  <label for="myName">告诉我你的名字：</label>
  <input id="myName" name="name" value="John">
  <input type="submit" value="提交">
</form>
```



```js
var FD  = new FormData(form);
```



#### 发送二进制数据

如果你用来初始化[`formData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)对象的那个表单中包含了一个文件输入框(type=file的input元素),则在发送AJAX时,用户在这个文件输入框中选定的文件也会被发送,和正常的表单提交一样.而且即使你没有用表单初始化这个formData对象,你同样可以手动向这个formData对象中添加若干个二进制数据.



二进制数据的来源主要有三种:[`FileReader`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader) API,[`Canvas`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement) API,[WebRTC](https://developer.mozilla.org/zh-CN/docs/WebRTC/navigator.getUserMedia) API.不幸的是,在一些旧的浏览器中,我们没有能力访问二进制数据,或者需要一些很繁杂的解决办法才能实现.访问二进制数据已经超出了本文的介绍范围.如果你想知道更多关于`FileReader` API的知识,你可以阅读:[如何在web应用程序中使用文件](https://developer.mozilla.org/zh-CN/docs/Using_files_from_web_applications).

使用[`formData`](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/FormData)发送二进制数据非常简单,只需要调用`append方法将你需要发送的File对象或者Blob对象添加进去`.