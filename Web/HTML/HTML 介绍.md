
# 1 HTML 是什么？

HTML （超文本标记语言--HyperText Markup Language）是构成Web世界的一砖一瓦。它描述并定义了一个网页的内容和基本布局。对应的 CSS 是定义了页面的展示效果，JS 是定义了页面的交互功能。具体的说就是：

1. 通过使用不同的文档元素，使普通文本具有特殊语义。

2. 将文档结构化为逻辑块。

3. 正是这个结构化文件告诉了浏览器应该如何构造一个页面。


HTML 的特点：

1. HTML 不是一种编程语言，它是一种标记语言，用于告诉浏览器该如何构造页面。
2. HTML 由一系列**元素**组成。

## 1.1 HTML 元素概念


### 元素的主要组成部分：

* 开始标签（Opening tag）：包括元素的名称和符号，例如：&lt;p&lt;。
* 结束标签（Closing tag）：这与开始标记相同，只是除了元素名称还包含正斜杠 &lt;/p&gt;。
* 内容（Content）：元素的内容。
* 元素（Element）：开始标记，加结束标记，加内容，等于元素。


### 嵌套元素

元素放到其它元素之中——这被称作嵌套。


### 块级元素和内联元素

HTML中需要知道的两种重要的元素类别，块级元素和内联元素。

* 块级元素在页面中以块的形式展现 —— 相对与其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。块级元素通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。一个以block形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。
* 内联元素通常出现在块级元素中并包裹文档内容的一小部分，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素<a&gt;或者强调元素&lt;em&gt;和 &lt;strong&gt;。


### 空元素

有些元素并不具有开始标签，内容和结束标记，自由一个标签通常用来在此元素所在的位置插入/嵌入一些东西，例如 &lt;img src="a.png"&lt;


## 1.2 属性


属性包含元素的额外信息，这些信息不会出现在实际的内容中。可以被用来识别此元素的样式信息或其他信息。


一个属性必须包含如下内容：

1. 元素和属性之间有空格分割
2. 属性后面紧跟一个“=”符号。
3.有一个属性值，由一对引号""引用。



### 布尔属性

例如 disabled 属性， 有时候你会看到它是没有属性值的，这也是合法的，这种属性被称为布尔属性，它们只能有跟它的属性名一样的属性值。例如：

	<input type="text" disabled="disabled">
	
或者更简洁的写法

	<input type="text" disabled>
	
	
### 省略包围属性值的引号

当你浏览那些粗糙的web网站，你将会看见各种各样奇怪的标记风格，其中就有不给属性值添加引号。在某些情况下它是被允许的，但是其他情况下会破坏你的标记。 例如：

	<a href=https://www.mozilla.org/ title=The Mozilla homepage>favorite website</a>
	
此时的title已经无法正确获取了。



### 单引号或者双引号？？

 都可以用，看你心情，不过不能混用。
 

## 1.3 分析 HTML 文档

了解整个 HTML 文档的结构。

	<!DOCTYPE html>
	<html>
	  <head>
		<meta charset="utf-8">
		<title>My test page</title>
	  </head>
	  <body>
		<p>This is my page</p>
	  </body>
	</html>

	

	1. <!DOCTYPE html>: 声明文档类型.
	2. <html&lt;</html>: <html>元素。这个元素包裹了整个完整的页面，是一个根元素。
	3. <head></head>: <head>元素. 这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等等。
	4. <meta charset="utf-8">: 这个元素设置文档使用utf-8字符集编码。
	5. <title&lt;</title>: 设置页面标题。
	6. <body&lt;</body>: <body>元素。 包含了你访问页面时所有显示在页面上的内容。


### HTML中的空白


HTML 解释器会将连续出现的空白字符减少为一个单独的空格符。


### 特殊字符


在HTML中，字符 &lt;, &lt;,",' 和 & 是特殊字符. 它们是HTML语法自身的一部分, 

原义字符	等价字符引用
&lt;			&lt;
&lt;			&gt;
"			&quot;
'			&apos;
&			&amp;
	
### 注释

 注释是被浏览器忽略的，而且是对用户不可见的，
 
 
	<!-- <p>I am!</p> -->
	



## 2 什么是 HEAD 标签？ 


* 作用是包含一些页面元数据、标题、CSS JS 链接等页面信息。
* 特点是其内容不会再浏览器中显示。


**HEAD 中包含的内容及其主要功能如下：**

### 2.1 为页面设置标题

	<title>My test page</title>
	
	

### 2.2 HTML 中的元数据 &lt;meta&gt;  元素

元数据就是描述数据的数据。HTML 元数据是作为 HTML **页面的级别** 的元数据的存在。 HTML有一个“官方的”方式来为一个**文档**添加元数据，——  	&lt;meta&gt; 元素.

例如指定字符集：

	<meta charset="utf-8"> 

或者你也可以指定你自己的元数据
	
	<meta name="mx-title" content="特殊标题"> 

	
	
许多 &lt;meta&gt; 元素包含了name 和 content 特性:

* name 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。
* content 指定了实际的元数据内容。



一些常用的元数据包括：

* 添加作者和描述:

		<meta name="author" content="Chris Mills">
		
		
* 对于 name 为 description 的 meta 元素中的数据将会被搜索引擎用于显示在搜索列表。
		
		<meta name="description" content="The MDN Learning Area aims to provide complete beginners to the Web with all they need to know to get started with developing web sites and applications.">
		
	
### 2.3 点自定义图标

通常会以一个16x16像素的 ico 格式的图片作为一个网站的图标，显示在浏览器标签上。

图片的格式也可以是 png 和 jpg 但是 ico 格式的兼容性最好，甚至包括 IE6。


	<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
	
	
### 2.4 在 HTML 中使用 CSS 和 JavaScript

使用 link 和 script 元素引入 样式和 js。


### 2.5 为文档设置主语言

	<html lang="en-US">

### 2.6 &lt;base&gt; 元素

	<base> 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:


	

## 3 HTML 文字处理基础

HTML 的主要工作就是编辑文本结构和文本内容，以便在浏览器上正确的显示。本章介绍了适用于文本的不同结构元素。


**文档结构化**的意义相当明显，未经结构化处理的一段文本，被浏览器处理后将编程一大段只包含空格的文本内容，根本没有可读性。而经过结构化的文本则会被浏览器正确的显示。在结构化的同时还要尽可能的**语义化**。以便当我们看到这个结构就能大概明白这段文本的显示结果。

**结构化和语义化是文档处理的两大要素。**

* 语义对可访问性，SEO（搜索引擎优化）等非常重要。


接下来是一些基本元素的介绍:

### 3.1 &lt;p&gt; 标签、&lt;h&gt; 标签

h 标签和 p 标签是基本的文本处理元素，但是也可以使用其他元素扩展更为丰富的语义。

### 3.2 列表标签

HTML 中存在三种不同类型的列表：

两种基本列表， 无序列表、有序列表。一种描述列表。

* 无序列表 
	
		<ol>
			<li>苹果</li>
			<li>栗子</li>
		</ol>
	
* 有序列表
		
		<ul>
			<li>1</li>
			<li>2</li>
			<li>3</li>
		</ul>
		

嵌套列表
	
		<ol>
			<li>苹果
				<ul>
					<li>1</li>
					<li>2</li>
					<li>3</li>
				</ul>
			</li>
			<li>栗子
				<ul>
					<li>1</li>
					<li>2</li>
					<li>3</li>
				</ul>
			</li>
		</ol>


### 3.3 重点强调

#### 3.3.1 &lt;em&gt; 斜体

<p>I am <em>glad</em> you weren't <em>late</em>.</p>

	<p>I am <em>glad</em> you weren't <em>late</em>.</p>

#### 3.3.2 &lt;strong&gt; 加粗字体

<p>This liquid is <strong>highly toxic</strong>.</p>

<p>I am counting on you. <strong>Do not</strong> be late!</p>

	<p>This liquid is <strong>highly toxic</strong>.</p>

	<p>I am counting on you. <strong>Do not</strong> be late!</p>	
#### 3.3.3 斜体字、粗体字、下划线...

* &lt;b&gt; : 被用来传达传统上用斜体表达的意义：外国文字，分类名称，技术术语，一种思想……
* &lt;i&gt; : 被用来传达传统上用粗体表达的意义：关键字，产品名称，引导句……
* &lt;u&gt; : 被用来传达传统上用下划线表达的意义：专有名词，拼写错误……


**小结：**这一章包含了一些简单的语义元素，在这一领域还有更多的语义元素，在后续的整理中继续。。。



## 4 超链接

超链接非常重要 ——它们使互联网成为一个互联的网络。


### 4.1 链接的解析

通过将文本（或其他内容，见块级链接)转换为&lt;a&gt;元素内的链接来创建基本链接

#### 4.1.1 使用title属性添加支持信息

#### 4.1.2 块级链接

如上所述，你可以将一些内容转换为链接，甚至是 块级元素。如果你想要将一个图像转换为链接，你只需把图像放到&lt;a&gt;&lt;/a&gt;标签中间。

	<a href="https://www.mozilla.org/en-US/">
	  <img src="mozilla-image.png" alt="mozilla logo that links to the mozilla homepage">
	</a>

### 4.2 统一资源定位器（URL）与路径（PATH）

* 统一资源定位器（英文：Uniform Resource Locator，简写：URL）是一个定义了在网络上的位置的一个文本字符串。

* 路径指定文件系统中您感兴趣的文件所在的位置
	* 指向相同目录
	* 指向子级目录
	* 指向上级目录

#### 4.2.1 文档片段

超链接可以链接到html文档的特定部分（被称为文档片段），而不仅仅是文件的顶部。

为指定元素指定id

	<h2 id="Mailing_address">Mailing address</h2>

然后链接到那个特定的id，您可以在URL的结尾包含它，前面是一个井号（#）
	
	<p>Want to write us a letter? Use our <a href="contacts.html#Mailing_address">mailing address</a>.</p>
	

或者可以用它自己的文档片段参考链接到同一份文件的另一部分：

	<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>


#### 4.2.2 绝对链接和相对链接
#### 4.2.3 尽可能使用相对链接
#### 4.2.4 链接到非html资源 ——留下清晰的指示
#### 4.2.5 在下载链接时使用下载属性


### 4.3 电子邮件链接

其最基本和最常用的使用形式为一个mailto:link （链接），链接简单说明收件人的电子邮件地址。例如:

<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
	
	<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
	
这是一个仅提供收件人地址的链接，同时你还可以通过该链接提供更丰富的信息。

下面是一个包含cc、bcc、主题和主体的示例：

		<a href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&amp;subject=The%20subject%20of%20the%20email &amp;body=The%20body%20of%20the%20email">
	  Send mail with cc, bcc, subject and body
	</a>

超链接并表面上那么简单，他有更详细的规则和丰富的表现形式



## 5 高级文字格式



### 5.1 描述列表,即每一行包含实体部分和描述部分，如下：

		<dl>
		  <dt>soliloquy</dt>
		  <dd>In drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience (but not to other characters.)</dd>
		  <dt>monologue</dt>
		  <dd>In drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.</dd>
		  <dt>aside</dt>
		  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of additional background information.</dd>
		</dl>


<dl>
  <dt>soliloquy</dt>
  <dd>In drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience (but not to other characters.)</dd>
  <dt>monologue</dt>
  <dd>In drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.</dd>
  <dt>aside</dt>
  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought or piece of additional background information.</dd>
</dl>


**请注意：一个术语&lt;dt&gt;可以同时有多个描述&lt;dd&gt;**

### 5.2 块引用

HTML 也有用于标记引用的特性，引用区分于块应用和行引用，分别使用不同的元素。

#### 5.2.1 块引用

使用 &lt;blockquote&gt; 实现块引用，其中cite属性里用URL来指向引用的资源：

	<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
	  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
	  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
	</blockquote>


<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>

#### 5.2.2 行引用

使用 &lt;q&gt; 标签实现行引用，同样有 cite 属性：
	
	<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
	for short quotations that don't require paragraph breaks.</q></p>

浏览器默认将其作为普通文本放入引号内表示引用，表现如下：

<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q></p>

### 5.3 缩略语

&lt;abbr&gt;——它常被用来包裹一个缩略语或缩写，并且提供缩写的解释（包含在title属性中），例如：

	<p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to structure our web documents.</p>


<p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to structure our web documents.</p>


### 5.4 标记联系方式

address 元素用于标记联系方式

	<address>
	  <p>Chris Mills, Manchester, The Grim North, UK</p>
	</address>

<address>
  <p>Chris Mills, Manchester, The Grim North, UK</p>
</address>


### 5.5 上标（sup）和下标（sub）

	<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
	<p>Caffeine's chemical formula is C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.</p>
	<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>

<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>Caffeine's chemical formula is C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>


### 5.6 展示计算机代码

* code: 用于标记计算机通用代码。
* pre: 对保留的空格（通常是代码块）——如果您在文本中使用缩进或多余的空白，浏览器将忽略它，您将不会在呈现的页面上看到它。但是，如果您将文本包含在&lt;pre&gt;&lt;/pre&gt;标签中，那么空白将会以与你在文本编辑器中看到的相同的方式渲染出来。
* var: 用于标记具体变量名。
* kbd: 用于标记输入电脑的键盘（或其他类型）输入。
* samp: 用于标记计算机程序的输出。


### 5.7 标记时间和日期

	<time datetime="2016-01-20">20 January 2016</time>
	

<time datetime="2016-01-20">20 January 2016</time>



## 6 文档与网站构架


除了定义网页的各个部分（例如“段落”或“图片”）外，HTML还拥有一些用于定义网站区域的块级元素(例如“头部”，“导航菜单”，“主要内容列”)。本文将探讨如何规划基本的网站结构，并通过编写HTML来表示这种网站结构。



### 6.1 文档的基本部

* 标题
* 导航
* 主要内容
* 侧栏
* 页脚


### 6.2 HTML 元素细节

一些主要的元素定义：

* main 展现了页面内容的独特性。
* article 闭合一块与自身相关的内容。
* section 具体的功能分区。
* aside 
* header 
	
	展现了一系列的介绍性内容。如果它是 body 的子元素,它就定义了网站的全局页眉。但是如果它是 article 或 section 的子元素，它就定义了这些部分的特定的页眉(不要把这些与titles and headings混淆)。
	
* nav 导航，二级链接等
* footer 页面的页脚


### 6.3 没有特定语义的修饰元素 div 和 span

div 是块级无语义元素。span 是行级无语义元素。

### 6.4 换行与水平分割线 br、hr

通过这一章，了解一基本的网页结构和语义。详细等标签和文档结构要做详细的整理。












**总结：**

**就整理目标来说，这一部分确实是基础的东西，虽然所有的东西都用过，也都看过，但是当把所有东西放在一起来讲时，便是系统化体现。**

**HTML 首先是简单的简单的结构化文本文档。其复杂性便在于如何更优美的实现结构化和语义化。由此延伸出来的学习目标便是从 HTML 的网页结构框架开始，逐个 HTML 网页的所有结构组成，最终使用这些语义化的结构任意的构建自己的网站。**

**学习之道：当你深刻的理解了每一个基础的知识，那么招式便显得顺理成章**





